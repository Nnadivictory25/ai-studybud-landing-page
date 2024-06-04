<script lang="ts">
	import { CircleUser, Bot } from 'lucide-svelte';
	import { onMount } from 'svelte';
	import { backOut } from 'svelte/easing';
	import { fly } from 'svelte/transition';
	let fileFormats = ['pdf', 'ppt', 'doc', 'png', 'jpg', 'txt'];

	let conversation = [
		{
			role: 'user',
			message: 'Can you summarize this document?'
		},
		{
			role: 'ai',
			message: 'Sure! Here is a summary of the document...'
		}
	];
</script>

<div class="mt-14 space-y-24 md:px-24">
	<div class="getStarted ctn">
		<div class="left stepCtn">
			<span class="step">1. Get Started</span>
			<h2>Sign Up</h2>
			<p>
				Click on the <span class="font-semibold">"Get Started"</span> button to create your account and
				start using AI Studybud for free.
			</p>
		</div>
		<div class="right assetCtn">
			<a
				href="https://app.aistudybud.online/"
				class="btn mx-auto !mt-5 block w-[70%] animate-bounce border-gray-800 bg-black px-4 py-3 text-center text-base shadow-lg md:mx-0 md:w-fit md:text-lg"
				>Get Started Now</a
			>
		</div>
	</div>

	<div class="upload ctn">
		<div class="left uploadCtn assetCtn gradient-bg flex items-center md:gap-3">
			{#each fileFormats as file}
				<img src="/{file}.webp" alt={file} class="w-12" width="48" height="48" />
			{/each}
		</div>

		<div class="right stepCtn">
			<span class="step">2. Upload</span>
			<h2>Upload File</h2>
			<p>
				In the dashboard, click on the <span class="font-semibold">"Upload"</span> button to upload your
				documents. You can upload PDFs, Word documents, Images, and TXT files.
			</p>
		</div>
	</div>

	<div class="ask ctn">
		<div class="left stepCtn">
			<span class="step">3. Ask AI</span>
			<h2>Ask your AI Studybud anything!</h2>
			<p>
				After uploading your documents, you can ask your AI Studybud anything you want. It will
				provide you with the most relevant answer you need.
			</p>
		</div>
		<div class="right mt-3 flex h-[170px] w-full flex-col gap-4 md:mt-0">
			{#each conversation as { role, message }, i (i)}
				<div class="chat-message {role}">
					{#if role === 'user'}
						<CircleUser class="h-6 w-6 text-primary" />
					{:else}
						<Bot class="h-6 w-6 text-primary" />
					{/if}
					{message}
				</div>
			{/each}
		</div>
	</div>
</div>

<style lang="scss">
	h2 {
		@apply text-lg font-bold md:text-2xl;
	}

	.step {
		@apply rounded-full bg-blue-200 px-3 py-1 text-sm font-medium shadow;
	}

	.stepCtn {
		@apply space-y-2;
	}

	.ctn {
		@apply grid gap-3 md:grid-cols-2 md:gap-36;
	}

	.assetCtn {
		background-image: linear-gradient(
			180deg,
			rgba(149, 97, 246, 0.1) 0%,
			rgba(235, 245, 247, 0.1) 100%
		);

		@apply flex h-[170px] w-full items-center justify-center rounded-lg;
	}
</style>
