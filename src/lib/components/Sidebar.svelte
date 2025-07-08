<script>
  import { onMount } from 'svelte';
  import { fly } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';

  let mounted = false;
  let activeSection = 'Hero';
  let isMobileMenuOpen = false;

  const navItems = [
    { id: 'Hero', label: 'About', href: '#Hero' },
    { id: 'Projects', label: 'Projects', href: '#Projects' },
    { id: 'Research', label: 'Research', href: '#Research' },
    { id: 'Contact', label: 'Contact', href: '#Contact' }
  ];

  onMount(() => {
    mounted = true;

    const observer = new IntersectionObserver(
      (entries) => {
        for (const entry of entries) {
          if (entry.isIntersecting) {
            activeSection = entry.target.id;
          }
        }
      },
      {
        root: null,
        rootMargin: '0px 0px -40% 0px',
        threshold: 0.05
      }
    );

    navItems.forEach(({ id }) => {
      const el = document.getElementById(id);
      if (el) observer.observe(el);
    });

    return () => observer.disconnect();
  });

  const scrollToSection = (href) => {
    const el = document.querySelector(href);
    if (el) {
      setTimeout(() => {
        el.scrollIntoView({ behavior: 'smooth', block: 'start' });
        isMobileMenuOpen = false; // close mobile dropdown after click
      }, 800);
    }
  };
</script>

<!-- Desktop Sidebar -->
{#if mounted}
  <aside
    class="fixed left-0 top-0 h-full w-64 hidden md:flex flex-col items-start justify-center bg-[#0F0F0F] z-25"
    in:fly={{ x: -100, duration: 600, easing: quintOut }}
  >
    <div class="relative pl-12">
      <div class="absolute right-0 top-0 h-full w-[3px] bg-[#005B41]"></div>
      <nav class="space-y-12 pr-6">
        {#each navItems as item}
          <button
            on:click={() => scrollToSection(item.href)}
            class="block text-left text-2xl font-semibold w-full transition-colors duration-300 
              {activeSection === item.id ? 'text-white' : 'text-[#888] hover:text-white'}"
          >
            {item.label}
          </button>
        {/each}
      </nav>
    </div>
  </aside>
{/if}

<!-- Mobile Menu Toggle Button -->
<div class="md:hidden fixed top-4 left-4 z-50">
  <button
    on:click={() => (isMobileMenuOpen = !isMobileMenuOpen)}
    class="bg-[#0F0F0F] border border-[#005B41] p-2 rounded-md flex flex-col justify-center items-center space-y-[4px]"
  >
    <!-- Hamburger lines -->
    <span class="w-6 h-[2px] bg-[#005B41]"></span>
    <span class="w-6 h-[2px] bg-[#005B41]"></span>
    <span class="w-6 h-[2px] bg-[#005B41]"></span>
  </button>
</div>

<!-- Mobile Dropdown Menu -->
{#if isMobileMenuOpen}
  <div
    class="fixed top-16 left-4 right-4 bg-[#0F0F0F] rounded-xl p-4 z-50 flex flex-col gap-4 md:hidden"
    transition:fly={{ y: -20, duration: 300 }}
  >
    {#each navItems as item}
      <button
        on:click={() => scrollToSection(item.href)}
        class="text-left text-lg font-medium transition-colors duration-300 
          {activeSection === item.id ? 'text-white' : 'text-[#aaa] hover:text-white'}"
      >
        {item.label}
      </button>
    {/each}
  </div>
{/if}
