<script lang="ts">
	import AnimatedChat from '$lib/components/animated-chat.svelte';
	import { Sparkles } from 'lucide-svelte';
	import IntersectionObserver from 'svelte-intersection-observer';
	import { backOut } from 'svelte/easing';
	import HowItWorks from '$lib/components/how-it-works.svelte';
	import { fade, fly } from 'svelte/transition';

	const whyUs = [
		{
			title: 'Precise Answers from Your Notes',
			description:
				'Ask any question about your uploaded documents and get direct, accurate answers saving so much research time.',
			icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-file-search"><path d="M14 2v4a2 2 0 0 0 2 2h4"/><path d="M4.268 21a2 2 0 0 0 1.727 1H18a2 2 0 0 0 2-2V7l-5-5H6a2 2 0 0 0-2 2v3"/><path d="m9 18-1.5-1.5"/><circle cx="5" cy="14" r="3"/></svg>'
		},

		{
			title: 'Upload of Various File Formats',
			description:
				'Upload PDFs, Word documents, Images and plain text for versatile study support.',
			icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-library-big"><rect width="8" height="18" x="3" y="3" rx="1"/><path d="M7 3v18"/><path d="M20.4 18.9c.2.5-.1 1.1-.6 1.3l-1.9.7c-.5.2-1.1-.1-1.3-.6L11.1 5.1c-.2-.5.1-1.1.6-1.3l1.9-.7c.5-.2 1.1.1 1.3.6Z"/></svg>'
		},

		{
			title: 'Customized Study Guides',
			description:
				'Personalized guides to help you focus on key concepts and areas needing improvement.',
			icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-notebook-pen"><path d="M13.4 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2v-7.4"/><path d="M2 6h4"/><path d="M2 10h4"/><path d="M2 14h4"/><path d="M2 18h4"/><path d="M18.4 2.6a2.17 2.17 0 0 1 3 3L16 11l-4 1 1-4Z"/></svg>'
		},

		{
			title: 'Interactive Quizzes',
			description: 'Test your knowledge with quizzes tailored to your study materials.',
			icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-brain"><path d="M12 5a3 3 0 1 0-5.997.125 4 4 0 0 0-2.526 5.77 4 4 0 0 0 .556 6.588A4 4 0 1 0 12 18Z"/><path d="M12 5a3 3 0 1 1 5.997.125 4 4 0 0 1 2.526 5.77 4 4 0 0 1-.556 6.588A4 4 0 1 1 12 18Z"/><path d="M15 13a4.5 4.5 0 0 1-3-4 4.5 4.5 0 0 1-3 4"/><path d="M17.599 6.5a3 3 0 0 0 .399-1.375"/><path d="M6.003 5.125A3 3 0 0 0 6.401 6.5"/><path d="M3.477 10.896a4 4 0 0 1 .585-.396"/><path d="M19.938 10.5a4 4 0 0 1 .585.396"/><path d="M6 18a4 4 0 0 1-1.967-.516"/><path d="M19.967 17.484A4 4 0 0 1 18 18"/></svg>'
		},

		{
			title: 'Summarization of Documents',
			description: 'Quickly review important points with concise summaries of lengthy documents',
			icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-badge-info"><path d="M3.85 8.62a4 4 0 0 1 4.78-4.77 4 4 0 0 1 6.74 0 4 4 0 0 1 4.78 4.78 4 4 0 0 1 0 6.74 4 4 0 0 1-4.77 4.78 4 4 0 0 1-6.75 0 4 4 0 0 1-4.78-4.77 4 4 0 0 1 0-6.76Z"/><line x1="12" x2="12" y1="16" y2="12"/><line x1="12" x2="12.01" y1="8" y2="8"/></svg>'
		},

		{
			title: 'Access to Fine-tuned Model',
			description:
				'Get access to a fine-tuned model trained to be your smart all-knowing study buddy',
			icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-bot-message-square"><path d="M12 6V2H8"/><path d="m8 18-4 4V8a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2Z"/><path d="M2 12h2"/><path d="M9 11v2"/><path d="M15 11v2"/><path d="M20 12h2"/></svg>'
		}
	];

	let imgCtn: HTMLDivElement;
	let whyUsCtn: HTMLElement;
</script>

<section id="hero">
	<div class="left">
		<span class="tag">
			<Sparkles strokeWidth="1" class="w-5 text-primary md:w-auto " />
			<p>Your Smart AI Study Buddy</p>
		</span>

		<h1>Get Precise Answers from Your Notes</h1>
		<p class="sub">
			AI Studybud helps you learn the important concepts without wasting time on boring notes.
		</p>

		<a
			href="https://app.aistudybud.online/"
			class="btn mx-auto !mt-5 block w-full px-4 py-3 text-center text-base md:mx-0 md:w-fit md:text-lg"
			>Get Started Now</a
		>
		<div class="tag mt-5 flex items-center gap-4 font-semibold">
			<div class="users flex items-center -space-x-6">
				<img width="50" height="50" src="/user1.webp" alt="user 1" />
				<img width="50" height="50" src="/user2.webp" alt="user 2" />
				<img width="50" height="50" src="/user3.webp" alt="user 3" />
			</div>
			<p class="whitespace-nowrap">
				Trusted by <span class="font-bold text-primary">5000+</span> students
			</p>
		</div>
	</div>
	<div class="right">
		<AnimatedChat />

		<IntersectionObserver once element={imgCtn} let:intersecting>
			<div bind:this={imgCtn}>
				{#if intersecting}
					<img class="student-img" src="/student.webp" alt="student" in:fade={{ duration: 1000 }} />
				{/if}
			</div>
		</IntersectionObserver>
	</div>
</section>

<section id="whyUs" class="min-h-screen pb-7 pt-14 md:min-h-[65vh]">
	<IntersectionObserver once threshold={0.3} element={whyUsCtn} let:intersecting>
		<h2>Why use AI Studybud?</h2>

		<div bind:this={whyUsCtn} class="mt-10 grid gap-8 md:grid-cols-3 md:px-24">
			{#each whyUs as { title, description, icon }, i (i)}
				{#if intersecting}
					<div
						in:fly={{ y: 45, duration: 500, delay: 100 * i, easing: backOut }}
						class="whyUs flex h-full gap-2"
					>
						<div class="text-primary">
							{@html icon}
						</div>
						<div class="content">
							<h3 class="pb-1 font-bold">{title}</h3>
							<p>{description}</p>
						</div>
					</div>
				{/if}
			{/each}
		</div>
	</IntersectionObserver>
</section>

<section id="howItWorks" class="pt-16">
	<h2>How it works</h2>
	<p class="text-center">Using AI Studybud is very simple.</p>

	<HowItWorks />
</section>

<style>
	#hero {
		position: relative;
		min-height: 100vh;
		overflow: hidden; /* Ensure the pseudo-element doesn't cause scrolling issues */

		@apply grid pt-36 md:grid-cols-2 md:pt-40;
	}

	#hero::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: #e5e5f7;
		opacity: 0.1;
		background-image: linear-gradient(#c5c5c5 4px, transparent 4px),
			linear-gradient(to right, #bbbbbb 4px, #e5e5f7 4px);
		background-size: 80px 80px;
		z-index: 0;
	}

	#hero .left {
		position: relative;
		z-index: 1;

		@apply md:w-[93%];
	}

	#hero .right {
		position: relative;
		z-index: 1;
	}

	.tag {
		@apply mb-4 flex w-fit items-center gap-2 rounded-full border border-primary bg-purple-300 bg-opacity-20  px-5 py-1 text-sm font-semibold  md:text-base;
	}

	h1 {
		@apply text-3xl font-extrabold md:text-5xl md:tracking-tight;
	}

	.sub {
		@apply pt-3 text-left text-lg font-medium text-gray-700;
	}

	.student-img {
		@apply absolute -bottom-4 -right-24 w-[250px] md:w-auto;
	}

	.users img {
		@apply h-[40px] w-[40px] rounded-full ring ring-primary-light md:h-[50px] md:w-[50px];
	}

	section h2 {
		@apply text-center text-2xl font-extrabold md:text-3xl  md:tracking-tight;
	}

	#whyUs {
		background-color: #8ec5fc;
		background-image: linear-gradient(70deg, #d6eaff 0%, #f3e6ff 100%);
	}
</style>
