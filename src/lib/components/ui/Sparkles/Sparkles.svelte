<script>
	import { cn } from '@/lib/utils/cn';
	import { Motion } from 'svelte-motion';

	export let minSize = 1;
	export let maxSize = 2;
	export let particleColor = '#ffffff';
	export let particleDensity = 100;
	export let className = undefined;

	function getRandomValue(min, max) {
		return min + Math.random() * (max - min);
	}

	const sparkles = Array.from({ length: particleDensity }, () => ({
		id: crypto.randomUUID(),
		top: `${Math.random() * 100}%`,
		left: `${Math.random() * 100}%`,
		size: getRandomValue(minSize, maxSize),
		delay: Math.random() * 5,
		duration: getRandomValue(2, 5),
		opacity: getRandomValue(0.1, 0.7)
	}));
</script>

<div class={cn('fixed inset-0 w-full h-full z-0 pointer-events-none', className)}>
	{#each sparkles as s (s.id)}
		<Motion
			let:motion
			initial={{ opacity: 0, scale: 0.8 }}
			animate={{
				opacity: [0, s.opacity, 0],
				scale: [0.8, 1.2, 0.8]
			}}
			transition={{
				duration: s.duration,
				repeat: Infinity,
				repeatDelay: s.delay,
				ease: 'easeInOut'
			}}
		>
			<span
				use:motion
				class="absolute rounded-full"
				style={`
					width: ${s.size}px;
					height: ${s.size}px;
					background-color: ${particleColor};
					top: ${s.top};
					left: ${s.left};
				`}
			></span>
		</Motion>
	{/each}
</div>
