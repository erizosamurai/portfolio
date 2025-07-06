<script>
  import { fade } from 'svelte/transition';

  import Contact from '$lib/components/Contact.svelte';
  import Hero from '$lib/components/Hero.svelte';
  import Projects from '$lib/components/Projects.svelte';
  import Research from '$lib/components/Research.svelte';
</script>

<!-- Page layout wrapper -->
<div class="min-h-screen flex flex-col">

  <!-- Hero with fade in -->
  <div transition:fade={{ delay: 100, duration: 600 }}>
    <Hero />
  </div>

  <!-- Main content area -->
  <div class="flex-grow">
    <div class="flex flex-col md:flex-row items-start justify-center px-6 lg:px-24 gap-12">
      
      <!-- Avatar spacing (left column) -->
      <div class="flex-shrink-0">
        <div class="w-40 h-0"></div>
      </div>

      <!-- Main content aligned to text column -->
      <div class="w-full max-w-2xl flex flex-col gap-10">
        <div transition:fade={{ delay: 300, duration: 600 }}>
          <Projects />
        </div>

        <div transition:fade={{ delay: 500, duration: 600 }}>
          <Research />
        </div>

        <div transition:fade={{ delay: 700, duration: 600 }}>
          <Contact />
        </div>

        <div transition:fade={{ delay: 900, duration: 600 }}>
          <footer class="mt-10 pb-12 text-sm text-[#B0B0B0]">
            Built using <span class="font-semibold text-[#005B41]">SvelteKit</span> and <span class="font-semibold text-[#005B41]">Tailwind</span>,  
            deployed with <span class="font-semibold text-[#005B41]">Vercel</span> by yours truly.
          </footer>
        </div>
      </div>
    </div>
  </div>
</div>
