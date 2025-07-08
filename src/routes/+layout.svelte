<script>
  import '../app.css';
  import Sparkles from '$lib/components/ui/Sparkles/Sparkles.svelte';
  import Sidebar from '$lib/components/Sidebar.svelte';
  let { children } = $props();
</script>

<!-- Full-page layout -->
<div class="relative min-h-screen flex bg-[#0F0F0F] text-white font-[Poppins]">
  <!-- Sidebar -->
  <Sidebar />

  <!-- Main content area -->
  <div class="flex-1 relative flex flex-col overflow-x-hidden mx-auto max-w-7xl px-6">
    <!-- Background Sparkles -->
    <Sparkles className="pointer-events-none z-0 absolute inset-0" />

    <!-- Page content -->
    <main class="relative z-10 flex-grow px-6 py-10 md:px-12 lg:px-20">
      {@render children()}
    </main>
  </div>
</div>