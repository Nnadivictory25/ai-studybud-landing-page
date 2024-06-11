<script lang="ts">
	import Marquee from 'svelte-fast-marquee';

	let testimonials = [
		{
			name: 'Berzan',
			title: 'College Student',
			uni: 'Akdeniz University, Turkey',
			testimony:
				'AI Study Bud is like a clone of myself who learns a topic and lets me ask him anything about it in a couple of seconds.',
			img: '/berzan.webp'
		},

		{
			name: 'Bethel',
			title: 'College Student',
			uni: 'Abia State University, Nigeria',
			testimony:
				'AI Studybud has helped me as an engineering student to dive deep into advanced topics and understand formulas better. I can even generate quizzes and test myself, insane!',
			img: '/bethel.webp'
		},

		{
			name: 'John',
			title: 'College Student',
			uni: 'Antalya Bilim University, Turkey',
			testimony:
				'Everything written about AI Studybud is true. It has helped me in my studies and has made my learning experience much more enjoyable and fun.',
			img: '/avatar.webp'
		},

		{
			name: 'Victory',
			title: 'College Student & Founder AI Studybud',
			uni: 'Abia State University, Nigeria',
			testimony:
				'I as a student had a hard time focusing while reading, I am not the patient reading type. I wanted a way to accelerate my learning and I thought of a tool that could find information for me fast from my university lecture notes, building this has helped me a lot as I get clarification on topics discussed in class later',
			img: '/founder.jpg'
		},

		{
			name: 'Favor',
			title: 'Post-graduate Student',
			uni: 'UK',
			testimony:
				'As a post-graduate student, I was struggling to keep up with the pace of my coursework. AI Studybud has been a game-changer for me. It has helped me to focus and has made my learning experience much more efficient. Writing my thesis was a breeze too !',
			img: '/favor.jpg'
		}
	];
</script>

<div class="hidden md:block">
	<Marquee
		gradient
		speed={25}
		gap={'2rem'}
		pauseOnHover
		class=" w-full items-center  py-10"
		style="--gradientColor: rgb(243 244 246); --gradientWidth: 2%;"
	>
		{#each testimonials as { name, title, uni, testimony, img }, i (i)}
			<div class="testimonial">
				<div class="absolute top-3 flex items-center">
					<img src="/star.webp" alt="star" width="20" height="20" />
					<img src="/star.webp" alt="star" width="20" height="20" />
					<img src="/star.webp" alt="star" width="20" height="20" />
					<img src="/star.webp" alt="star" width="20" height="20" />
					<img src="/star.webp" alt="star" width="20" height="20" />
				</div>
				<div class="text-center text-lg font-medium mt-3">
					<p>"{testimony}"</p>
				</div>
				<div class="flex flex-col items-start gap-3 text-left md:flex-row">
					<div class="avatar">
						<img
							src={img}
							alt={name}
							width="40"
							height="40"
							class="pb mt-1 rounded-full ring ring-primary"
						/>
					</div>
					<div>
						<h3 class="pt-1 md:pt-0">{name}</h3>
						<p class="font-medium text-gray-700">{title},</p>
						<p class="font-medium text-gray-700">{uni}</p>
					</div>
				</div>
			</div>
		{/each}
	</Marquee>
</div>

<div class="mt-7 space-y-5 md:hidden">
	{#each testimonials as { name, title, uni, testimony, img }, i (i)}
		<div class="testimonial">
			<div class="absolute top-3 flex items-center">
				<img src="/star.webp" alt="star" width="20" height="20" />
				<img src="/star.webp" alt="star" width="20" height="20" />
				<img src="/star.webp" alt="star" width="20" height="20" />
				<img src="/star.webp" alt="star" width="20" height="20" />
				<img src="/star.webp" alt="star" width="20" height="20" />
			</div>
			<div class="text-center text-lg font-medium">
				<p>"{testimony}"</p>
			</div>
			<div class="flex items-start gap-5 text-left md:flex-row">
				<div class="avatar">
					<img
						src={img}
						alt={name}
						width="40"
						height="40"
						class="pb mt-1 rounded-full ring ring-primary"
					/>
				</div>
				<div>
					<h3 class="pt-1 md:pt-0">{name}</h3>
					<p class="font-medium text-gray-600">{title},</p>
					<p class="font-medium text-gray-600">{uni}</p>
				</div>
			</div>
		</div>
	{/each}
</div>

<style lang="scss">
	.avatar {
		width: 40px;
		height: 40px;
	}

	.testimonial {
		@apply relative flex w-full max-w-sm flex-col gap-7 rounded-md border border-transparent bg-white p-5 pt-12 shadow transition-all hover:border-primary md:w-auto md:p-7;

		h3 {
			@apply font-semibold;
		}
	}
</style>
