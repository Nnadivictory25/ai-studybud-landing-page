<script lang="ts">
	import * as Accordion from '$lib/components/ui/accordion/index.js';

	const faqs = [
		{
			question: "There are many 'Chat PDF' AI products out there, how's this any different?",
			answer:
				"Well, that's right but this AI is Trained + Fine-tuned to be a study guide for students and not just based on generalisation. So it converses and acts like one. And also you don't only 'Chat with PDFs', you can also 'Chat with Word Documents, Images, Text Files, etc'."
		},
		{
			question: 'Can I cancel my subscription?',
			answer:
				'Of course! You can cancel anytime you want, just contact us and we will help you do it. No questions asked.'
		},
		{
			question: `Why won't I just use ChatGPT instead of this? What's the difference?`,
			answer: `You are not entirely wrong, but chatGPT is very limited if you are going to uplaod and enquire about your uploaded files. Well, unless you pay 20$/m for a chatGPT Plus account. But AI Studybud gives you access to almost unlimited chat with your uploaded files + it's cheaper .`
		},
		{
			question: 'Can I upload files other than PDFs?',
			answer: `Yes, you can upload any file format you want. We also support DOCX, PPT, TXT and Image files. (For paid plans only)`
		},
		{
			question: 'How many files can I upload?',
			answer:
				'On the free plan you can upload up to 2 files, but on the paid plans you can upload up to 50-100 files!'
		},
		{
			question: `Can the AI understand natural language?`,
			answer: `Yes, the AI can understand natural language. You can ask questions like "".`
		},
		{
			question: 'Can I also use this on my mobile?',
			answer: `Of course! This web application was built with mobile users in mind. The interface is easy to navigate and looks good even on your mobile device.`
		},
		{
			question: 'Is there a file size limit?',
			answer: 'Yes, 10mb on the free plan and up to 32mb on the paid plans.'
		}
	];
</script>

<div class="mt-5 md:px-24">
	<Accordion.Root>
		{#each faqs as { question, answer }, i (i)}
			<Accordion.Item value="item-{i + 1}" class="">
				<Accordion.Trigger class=" text-left font-semibold"
					><span class="w-[85%] md:w-auto">{question}</span></Accordion.Trigger
				>
				<Accordion.Content class="text-base text-black">
					{answer}
				</Accordion.Content>
			</Accordion.Item>
		{/each}
	</Accordion.Root>
</div>
