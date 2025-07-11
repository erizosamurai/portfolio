<script>
  import { onMount } from 'svelte';
  import { fade } from 'svelte/transition';

  import Contact from '$lib/components/Contact.svelte';
  import Hero from '$lib/components/Hero.svelte';
  import Projects from '$lib/components/Projects.svelte';
  import Research from '$lib/components/Research.svelte';

  let mounted = false;

  onMount(() => {
    mounted = true;
  });
</script>

{#if mounted}
  <div class="min-h-screen flex flex-col">

    <!-- Hero -->
    <div in:fade={{ duration: 1500, delay: 100 }}>
      <Hero />
    </div>

    <!-- Main content -->
    <div class="flex-grow">
      <div class="flex flex-col md:flex-row items-start justify-center px-6 lg:px-24 gap-12">
        
        <div class="flex-shrink-0">
          <div class="w-40 h-0"></div>
        </div>

        <div class="w-full max-w-3xl flex flex-col gap-y-8">

          <div in:fade={{ duration: 600, delay: 300 }}>
            <Projects />
          </div>

          <div in:fade={{ duration: 600, delay: 500 }}>
            <Research />
          </div>

          <div in:fade={{ duration: 600, delay: 700 }}>
            <Contact />
          </div>

          <div in:fade={{ duration: 600, delay: 900 }}>
            <footer class="mt-10 pb-12 text-[16px] text-[#7C7F85]">
              Built using <span class="font-semibold text-[16px] text-[#4AB0F7]">SvelteKit</span> and 
              <span class="font-semibold text-[16px] text-[#4AB0F7]">Tailwind</span>, deployed with 
              <span class="font-semibold text-[16px] text-[#4AB0F7]">Vercel</span> by yours truly.
            </footer>
          </div>

        </div>
      </div>
    </div>
  </div>
{/if}
