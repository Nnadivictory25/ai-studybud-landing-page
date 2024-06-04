<script>
	import { onMount } from 'svelte';
	import '../app.css';
	import { fly } from 'svelte/transition';

	let animate = false;

	onMount(() => {
		animate = true;
	});
</script>

<div class="">
	<header>
		{#if animate}
			<nav in:fly={{ y: -50, duration: 500 }}>
				<a href="/"> <img src="/main-logo.svg" alt="logo" width="200" height="200" /></a>

				<div class="links">
					<a href="#howItWorks">How it works</a>
					<a href="faqs">FAQs</a>
					<a href="#pricing">Pricing</a>
				</div>

				<a href="https://app.aistudybud.online" class="btn border-gray-800 bg-black">
					Try For Free</a
				>
			</nav>
		{/if}
	</header>

	<slot></slot>
</div>

<style>
	nav {
		@apply absolute inset-x-0 top-5 z-10 mx-auto flex w-[95%] items-center justify-between rounded-full border-2 bg-white pr-5 font-medium shadow-sm   md:w-[60%] md:pr-9;
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
</style>
