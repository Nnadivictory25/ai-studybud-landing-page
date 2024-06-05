<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import { Button } from '$lib/components/ui/button';
	import { BadgeCheck } from 'lucide-svelte';
	import { Switch } from '$lib/components/ui/switch';

	const plans = [
		{
			name: 'Free',
			price: { monthly: 0, yearly: 0 },
			isPopular: false,
			features: [
				`Upload up to 2 files`,
				`Upload only PDF files`,
				`Upload up to 10mb per file`,
				`Send 5 messages / day`,
				`Access to fine-tuned model`
			]
		},

		{
			name: 'Pro',
			price: { monthly: 10, yearly: 100 },
			isPopular: true,
			features: [
				`Upload up to 50 files`,
				`Upload only PDF files`,
				`Upload up to 32mb per file`,
				`Send 1000 messages / day`,
				`Access to fine-tuned model`,
				`Access to use NLP model in chat (eg: "What is in page 2 of this doc?")`,
				`Summarization`,
				`Test generation`
			]
		},

		{
			name: 'Plus',
			price: { monthly: 15, yearly: 150 },
			isPopular: false,
			features: [
				`Everything in Pro`,
				`Upload up to 100 files`,
				`Upload PDF, DOCX, PPT, TXT and Image files`,
				`Upload multiple images at once`
			]
		}
	];

	let isMonthly = true;
</script>

<div class="mt-14 flex items-center justify-center gap-2 text-lg font-bold md:mb-0">
	<span class={`${isMonthly ? 'text-black' : 'text-gray-500'}`}> Monthly </span>
	<Switch
		class="!outline-none"
		checked={!isMonthly}
		onCheckedChange={(checked) => (isMonthly = !checked)}
	/>
	<span class={` space-x-3 ${!isMonthly ? 'text-black' : 'text-gray-500'}`}>
		Yearly
		<span class={`${!isMonthly ? 'text-gray-700' : 'text-gray-400'}`}> (Save 20% !) </span>
	</span>
</div>

<div class="mt-10 flex flex-col justify-center gap-10 md:flex-row">
	{#each plans as plan, i (i)}
		<Card.Root
			class={`relative h-full w-full md:h-auto md:w-[35%] ${plan.isPopular ? 'bg-primary !text-white' : ''}`}
		>
			{#if plan.isPopular}
				<span
					class="absolute -top-3 right-1/2 translate-x-1/2 rounded-full bg-yellow-400 px-4 py-1 font-semibold text-black"
				>
					Most popular
				</span>
			{/if}
			<Card.Header class="flex justify-between">
				<Card.Title class="text-xl font-bold">{plan.name}</Card.Title>
				<Card.Description
					class={` ${plan.isPopular ? 'text-white' : 'text-black'} text-3xl font-extrabold`}
				>
					{#if isMonthly}
						<span>
							${plan.price.monthly}
							<span class={`text-base ${plan.isPopular ? 'text-gray-200' : 'text-gray-500'}`}
								>/month</span
							>
						</span>
					{:else}
						<span>
							${plan.price.yearly}
							<span class={`text-base ${plan.isPopular ? 'text-gray-200' : 'text-gray-500'}`}
								>/year</span
							>
						</span>
					{/if}
				</Card.Description>
			</Card.Header>
			<div class="mb-5 flex justify-center px-6">
				<a
					class={` flex h-12 w-full items-center justify-center rounded-md bg-primary text-base font-medium text-white  hover:opacity-90 ${plan.isPopular ? '!bg-white font-semibold !text-black' : ''}`}
					href="https://app.aistudybud.online/">Sign Up</a
				>
			</div>
			<Card.Content class="flex flex-col gap-4 font-medium">
				{#each plan.features as feature, i (i)}
					<div class="flex gap-2">
						<div class="text-green-500">
							<BadgeCheck />
						</div>
						<div>{feature}</div>
					</div>
				{/each}
			</Card.Content>
		</Card.Root>
	{/each}
</div>