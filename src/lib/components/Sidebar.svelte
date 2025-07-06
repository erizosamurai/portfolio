<script>
  import { page } from '$app/stores';
  import { derived } from 'svelte/store';
  import Icon from "@iconify/svelte";

  const navItems = [
    { label: 'About', href: '/about' },
    { label: 'Projects', href: '/projects' },
    { label: 'Research', href: '/research' },
    { label: 'Contact', href: '/contact' },
  ];

  const currentPath = derived(page, $page => $page.url.pathname);
</script>

<style>
  .sidebar {
    width: 220px;
    min-height: 100vh;
    background-color: var(--color-background);
    padding: 1rem 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-family: 'Poppins', sans-serif;
  }

  .icon-buttons {
    display: flex;
    gap: 1.6rem;
    justify-content: center;
    border: 1.68px solid var(--color-accent);
    border-radius: 6.72px;
    margin-bottom: 2rem;
    padding: 0.4rem 1.1rem;

  }



  .nav {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    width: 100%;
    padding-left: 2rem;
  }

  .nav-link {
    font-size: 20px;
    font-weight: 700;
    color: #808080;
    position: relative;
    transition: color 0.3s;
  }

  .nav-link.active {
    color: white;
  }

  .nav-link.active::before {
    content: '';
    position: absolute;
    left: -1.5rem;
    top: 0;
    height: 100%;
    width: 3px;
    background-color: var(--color-foreground);
    border-radius: 2px;
  }
</style>

<div class="sidebar">
  <!-- Social Icons -->
  <div class="icon-buttons" >
    <a href="https://github.com/erizosamurai" target="_blank" aria-label="GitHub">
      <Icon icon="tdesign:logo-github-filled" width="30" height="30" style="color: #008170" />
    </a>
    <a href="https://x.com/ErizoSamurai" target="_blank" aria-label="X">
      <Icon icon="prime:twitter" width="30" height="30" style="color: #008170" />
    </a>
    <a href="https://linkedin.com" target="_blank" aria-label="LinkedIn">
      <Icon icon="uiw:linkedin" width="30" height="30" style="color: #008170" />
    </a>
  </div>

  <div class="nav">
    {#each navItems as item}
      <a
        href={item.href}
        class="nav-link { $currentPath === item.href ? 'active' : '' }"
      >
        {item.label}
      </a>
    {/each}
  </div>
</div>
