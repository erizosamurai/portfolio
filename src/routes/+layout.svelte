<script>
  import '../app.css';
  import Sparkles from '$lib/components/ui/Sparkles/Sparkles.svelte';
  let { children } = $props();
</script>

<!-- Proper flex column layout to control scroll and footer alignment -->
<div class="relative min-h-screen flex flex-col overflow-hidden">

  <!-- Background visual -->
  <Sparkles className="pointer-events-none z-0 absolute inset-0" />

  <!-- Main page content -->
  <div class="relative z-10 flex-grow">
    {@render children()}
  </div>
</div>
