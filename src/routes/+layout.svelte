<script>
	import '../app.css';
	import Sparkles from '$lib/components/ui/Sparkles/Sparkles.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
	let { children } = $props();
</script>

{@render children()}




<div class="relative min-h-screen overflow-hidden">
	<!-- Sparkles in the background -->
	<Sparkles className="pointer-events-none z-0" />

</div>

