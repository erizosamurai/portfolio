<script>
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';

	let pubVisible = false;
	let blogVisible = false;

	let pubRef;
	let blogRef;

	onMount(() => {
		// Observe Publications
		if (pubRef) {
			const pubObserver = new IntersectionObserver(([entry]) => {
				if (entry.isIntersecting) {
					pubVisible = true;
					pubObserver.unobserve(pubRef);
				}
			}, { threshold: 0.1 });
			pubObserver.observe(pubRef);
		}

		// Observe Blogs
		if (blogRef) {
			const blogObserver = new IntersectionObserver(([entry]) => {
				if (entry.isIntersecting) {
					blogVisible = true;
					blogObserver.unobserve(blogRef);
				}
			}, { threshold: 0.1 });
			blogObserver.observe(blogRef);
		}
	});
</script>

	<!-- Publications -->
	{#if pubVisible}
		<div in:fly={{ y: 50, duration: 1500 }} class="text-[24px] sm:text-[30px] lg:text-[32px] font-bold text-[#F5F7FA]">
			Publications
		</div>
		<div
			in:fly={{ y: 50, duration: 1500 }}
			class="mt-5 border-[1.5px] border-dashed border-[#1E88E5] rounded-xl p-6 text-[#F5F7FA]"
		>
			<p class="text-[16px] sm:text-[17px] italic leading-relaxed text-gray-200">
				Simhadri, Adhit, M. Rishikesh, and M. Subramaniam.
				"13 Machine Learning in Phishing URL Detection: A Review of Recent Progress."
				<i>Power Energy and Secure Smart Technologies</i> (2025).
			</p>
		</div>
	{/if}

	<!-- Element to observe -->
	<div bind:this={pubRef} style="height: 1px;"></div>

	<!-- Blogs -->
	{#if blogVisible}
		<div in:fly={{ y: 50, duration: 1500 }} class="mt-10 text-[24px] sm:text-[30px] lg:text-[32px] font-bold text-[#F5F7FA]">
			Blogs
		</div>
		<div
			in:fly={{ y: 50, duration: 1500 }}
			class="mt-4 border-[1.5px] border-dashed border-[#1E88E5] rounded-xl p-4 sm:p-6 text-[#F5F7FA]"
		>
			<p class="text-[16px] sm:text-[17px] text-center text-gray-300">Coming Soon</p>
		</div>
	{/if}

	<!-- Element to observe -->
	<div bind:this={blogRef} style="height: 1px;"></div>


