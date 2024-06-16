<script>
	import { onMount } from 'svelte';
	import '../app.css';
	import { fly } from 'svelte/transition';

	let animate = false;

	onMount(() => {
		animate = true;
	});

	const title = 'AI Studybud - Your Smart Study Companion';
	const desc =
		'Enhance your learning with AI Studybud, your smart study companion. Upload courses, simplify hard concepts, ask questions, and get personalized assistance with AI';

	const keywords = [
		'Study with AI',
		'Studybuddy',
		'AI Quiz genearator',
		'PDF to Quiz app',
		'free PDF to Quiz app',
		'PDF to Quiz',
		'Quiz generator',
		'Quiz maker',
		'Flashcard maker',
		'Flashcard generator',
		'Essay writer',
		'PDF summarizer',
		'PDF summarization',
		'free ai studybuddy',
		'Studybuddy ai',
		'Studybud',
		'Studybud ai',
		'Online study help',
		'Study help online',
		'AI-powered study assistant',
		'Study partner AI',
		'Study partner',
		'study companion',
		'Study buddy',
		'ai study buddy',
		'ai study buddy free',
		'Smart study tool',
		'Study aid with AI',
		'AI for studying',
		'Online learning companion',
		'Study assistance app',
		'Intelligent study buddy'
	];
</script>

<svelte:head>
	<link rel="preload" href="/main-logo.png" as="image" />

	<title>{title}</title>
	<meta name="description" content={desc} />

	<meta property="og:url" content="https://www.aistudybud.online" />
	<meta property="og:type" content="website" />
	<meta property="og:title" content="{title}</title>" />
	<meta property="site_name" content="AI Studybud" />
	<meta property="og:description" content={desc} />
	<meta property="og:image" content="https://www.aistudybud.online/og.png" />

	<meta name="twitter:card" content="summary_large_image" />
	<meta property="twitter:domain" content="aistudybud.online" />
	<meta property="twitter:url" content="https://www.aistudybud.online" />
	<meta name="twitter:title" content="{title}</title>" />
	<meta name="twitter:description" content={desc} />
	<meta name="twitter:image" content="https://www.aistudybud.online/og.png" />

	<link rel="canonical" href="https://www.aistudybud.online" />
	<meta name="robots" content="index, follow" />
	<meta name="googlebot" content="index, follow" />
	<meta name="keywords" content={keywords.join(', ')} />
</svelte:head>

<div>
	<header>
		{#if animate}
			<nav in:fly={{ y: -50, duration: 500 }}>
				<a href="/"> <img src="/main-logo.png" alt="logo" width="200" /></a>

				<div class="links">
					<a href="#howItWorks">How it works</a>
					<a href="faqs">FAQs</a>
					<a href="#pricing">Pricing</a>
				</div>

				<a href="https://app.aistudybud.online" class="btn !border-gray-800 !bg-black">
					Try For Free</a
				>
			</nav>
		{/if}
	</header>

	<slot />

	<footer>
		<a href="/"> <img src="/main-logo.png" alt="logo" width="200" /></a>

		<div class="flex flex-col items-center gap-5 text-black md:flex-row">
			<a href="#faqs">FAQs</a>
			<a href="#pricing">Pricing</a>
			<a href="/privacy">Privacy Policy</a>
			<a href="/terms">Terms of Service</a>
		</div>
	</footer>
</div>

<style lang="scss">
	nav {
		@apply absolute inset-x-0 top-5 z-10 mx-auto flex h-[70px] w-[95%] items-center justify-between rounded-full border-2 bg-white pr-5 font-medium shadow-sm   md:w-[60%] md:pr-9;
	}

	nav img {
		@apply w-[190px] md:w-[220px];
	}

	.links {
		@apply hidden items-center gap-4 md:flex;
	}

	.links a {
		@apply text-gray-600 hover:text-black;
	}

	footer {
		@apply mx-auto flex flex-col justify-center gap-7 bg-white px-24 py-7 text-black md:max-w-4xl md:flex-row md:gap-20;

		a {
			@apply font-medium hover:underline;
		}
	}
</style>
