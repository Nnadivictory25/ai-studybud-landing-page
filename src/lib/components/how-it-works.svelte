<script lang="ts">
	import { onMount } from 'svelte';
	let fileFormats = ['pdf', 'ppt', 'doc', 'png', 'jpg', 'txt'];
</script>

<div class="mt-14 space-y-24 md:px-24">
	<div class="getStarted ctn">
		<div class="left stepCtn">
			<span class="step">Get Started</span>
			<h2>Sign Up</h2>
			<p class=" md:w-[65%]">
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
		<div class="left uploadCtn assetCtn flex items-center md:gap-3">
			{#each fileFormats as file}
				<img src="/{file}.webp" alt={file} class="w-12" />
			{/each}
		</div>

		<div class="right stepCtn">
			<span class="step">Upload</span>
			<h2>Upload File</h2>
			<p class=" md:w-[65%]">
				In the dashboard, click on the <span class="font-semibold">"Upload"</span> button to upload your
				documents. You can upload PDFs, Word documents, Images, and TXT files.
			</p>
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
		@apply grid gap-3 md:grid-cols-2 md:gap-24;
	}

	.getStarted > .right {
		background-image: linear-gradient(
			180deg,
			rgba(33, 212, 253, 0.7) 0%,
			rgba(235, 245, 247, 0.1) 100%
		);
	}

	.assetCtn {
		@apply flex h-[170px] w-full items-center justify-center rounded-lg;
	}

	.uploadCtn {
		background-image: linear-gradient(
			180deg,
			rgba(33, 212, 253, 0.7) 0%,
			rgba(235, 245, 247, 0.1) 100%
		);
	}
</style>
