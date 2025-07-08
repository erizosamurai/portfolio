<script>
  import { onMount } from 'svelte';
  import { fly } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';

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
    <section id="Hero" class="scroll-mt-32" in:fly={{ y: -30, duration: 600, delay: 100, easing: quintOut }}>
      <Hero />
    </section>

    <!-- Main content -->
    <div class="flex-grow min-h-screen">
      <div class="flex flex-col md:flex-row items-start justify-center px-6 lg:px-24 gap-12">

        <div class="flex-shrink-0">
          <div class="w-40 h-0"></div>
        </div>

        <div class="w-full max-w-2xl flex flex-col gap-10">

          <section id="Projects" class="scroll-mt-32" in:fly={{ y: 20, duration: 600, delay: 300, easing: quintOut }}>
            <Projects />
          </section>

          <section id="Research"  class="scroll-mt-32" in:fly={{ y: 20, duration: 600, delay: 500, easing: quintOut }}>
            <Research />
          </section>

          <section id="Contact" class="scroll-mt-32 ">
            <Contact />
          </section>

          <footer class="mt-10 pb-12 text-[14px] text-[#B0B0B0]">
            Built using <span class="font-semibold text-[#005B41]">SvelteKit</span> and
            <span class="font-semibold text-[#005B41]">Tailwind</span>, deployed with
            <span class="font-semibold text-[#005B41]">Vercel</span> by yours truly.
          </footer>

        </div>
      </div>
    </div>
  </div>
{/if}