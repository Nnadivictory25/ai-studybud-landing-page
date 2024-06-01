<script lang="ts">
	import { Bot, CircleUser } from 'lucide-svelte';
	import { onMount } from 'svelte';
	import { backOut } from 'svelte/easing';
	import { fly } from 'svelte/transition';

	const conversations = [
		{
			title: 'World War II History.pdf',
			conversations: [
				{ role: 'user', message: 'Where was World War II discussed in this course?' },
				{ role: 'AI', message: 'In pages 20, 21, and 22 of this document.' },
				{ role: 'user', message: 'Can you summarize the content related to World War II?' },
				{
					role: 'AI',
					message: "Sure! Here's a summary of World War II covered in pages 20, 21, and 22..."
				}
			]
		},
		{
			title: 'Mechanical Engineering 201.pdf',
			conversations: [
				{ role: 'user', message: 'How do I calculate the stress in a cantilever beam?' },
				{
					role: 'AI',
					message:
						'To calculate stress in a cantilever beam, you can use the formula σ = M*y / I, where σ is ...'
				},
				{ role: 'user', message: 'Could you explain how to find the moment of inertia?' },
				{
					role: 'AI',
					message: 'Of course! Moment of inertia depends on the shape of the cross-section...'
				}
			]
		},
		{
			title: 'Literary Analysis: Foreshadowing.txt',
			conversations: [
				{
					role: 'user',
					message: 'According to this novel, what does the foreshadowing of the storm signify?'
				},
				{
					role: 'AI',
					message:
						'According to this novel, the foreshadowing of the storm signifies impending danger and turmoil...'
				},
				{ role: 'user', message: 'Are there other instances of foreshadowing in this text?' },
				{
					role: 'AI',
					message: 'Yes, the author employs foreshadowing throughout the text to ...'
				}
			]
		},
		{
			title: 'Calculus Fundamentals.pdf',
			conversations: [
				{
					role: 'user',
					message: "I'm confused about the chain rule in calculus. Can you explain it?"
				},
				{
					role: 'AI',
					message:
						"The chain rule helps us differentiate composite functions. Let's break it down step by step."
				},
				{ role: 'user', message: 'I think I get it now. Thanks for clarifying!' },
				{ role: 'AI', message: "You're welcome! Don't hesitate to ask if you have more questions." }
			]
		}
	];

	let currentConversation = 0;

	function nextConversation() {
		animate = false;
		currentConversation++;
		if (currentConversation >= conversations.length) {
			currentConversation = 0;
		}

		setTimeout(() => (animate = true), 1000);
	}

	let animate = false;

	onMount(() => {
		animate = true;
		const interval = setInterval(() => {
			nextConversation();
		}, 15000);

		return () => {
			clearInterval(interval);
		};
	});
</script>

{#key currentConversation}
	<div class="chat-ctn" in:fly={{ y: -50, duration: 1000 }}>
		<p class="header">
			{conversations[currentConversation].title}
		</p>
		{#each conversations[currentConversation].conversations as { role, message }, i (i)}
			{#if animate}
				<div
					class="chat-message {role.toLowerCase()}"
					in:fly={{ y: 50, duration: 400, delay: 2000 * i, easing: backOut }}
				>
					{#if role === 'user'}
						<CircleUser class="h-6 w-6 text-primary" />
					{:else}
						<Bot class="h-6 w-6 text-primary" />
					{/if}
					{message}
				</div>
			{/if}
		{/each}
	</div>
{/key}

<style>
	.chat-ctn {
		@apply mt-7 flex h-[80vh] w-full flex-col gap-2 p-3 px-4 md:mt-0 md:h-auto;
	}

	.chat-message {
		@apply select-none rounded-md p-4 font-medium;
	}

	.chat-message.ai {
		background: rgba(105, 51, 207, 0.09);
		border-radius: 16px;
		box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
		backdrop-filter: blur(5.1px);
		-webkit-backdrop-filter: blur(5.1px);
		border: 1px solid rgba(105, 51, 207, 0.56);

		@apply md:w-[90%];
	}

	.chat-message.user {
		background: rgba(133, 74, 245, 0.23);
		border-radius: 16px;
		box-shadow: 0 4px 30px rgba(47, 47, 47, 0.1);
		backdrop-filter: blur(5.8px);
		-webkit-backdrop-filter: blur(5.8px);
		border: 1px solid rgba(72, 44, 124, 0.54);
		@apply self-end md:w-[90%];
	}

	.header {
		@apply select-none text-center font-medium text-primary;
	}
</style>
