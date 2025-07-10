<script>
  import Icon from '@iconify/svelte';
  import { fly } from 'svelte/transition';
  import { onMount } from 'svelte';

  let contactVisible = false;
  let contactRef;

  onMount(() => {
    if (contactRef) {
      const observer = new IntersectionObserver(([entry]) => {
        if (entry.isIntersecting) {
          contactVisible = true;
          observer.unobserve(contactRef);
        }
      }, { threshold: 0.1 });

      observer.observe(contactRef);
    }
  });
</script>

<!-- Trigger Observation -->
<div bind:this={contactRef} style="height: 1px;"></div>

<!-- Contact Section -->
{#if contactVisible}
  <div
    in:fly={{ y: 50, duration: 1500 }}
    class="w-full flex flex-col items-start gap-8 pt-20 text-white"
  >
    <div class="flex flex-col md:flex-row w-full justify-between gap-8">
      <!-- Text -->
      <div class="max-w-md">
        <h2 class="text-2xl sm:text-3xl lg:text-[32px] font-bold mb-4">Let’s work together</h2>
        <p class="text-[18px] leading-relaxed">
          I'm always looking for new opportunities and intriguing research projects.
          Feel free to contact me if you want to collaborate or just want to say hello.
        </p>
      </div>

      <!-- Social + Email -->
      <div class="flex flex-col gap-6 mt-16">
        <div class="flex gap-4">
          <a href="https://github.com/erizosamurai" target="_blank" rel="noopener noreferrer">
            <Icon icon="jam:github" width="28" height="28" class="text-[#008170]" />
          </a>
          <a href="https://x.com/ErizoSamurai" target="_blank" rel="noopener noreferrer">
            <Icon icon="prime:twitter" width="28" height="28" class="text-[#008170]" />
          </a>
          <a href="https://www.linkedin.com/in/adhitsimhadri/" target="_blank" rel="noopener noreferrer">
            <Icon icon="uiw:linkedin" width="28" height="28" class="text-[#008170]" />
          </a>
        </div>

        <div class="flex items-center gap-3 border border-dashed border-[#005B41] px-3 py-1 rounded-md w-fit">
          <Icon icon="mdi:email-outline" width="20" height="20" class="text-[#008170]" />
          <a href="mailto:adhit.simhadri@gmail.com" class="text-[16px]">
            adhit.simhadri@gmail.com
          </a>
        </div>
      </div>
    </div>
  </div>
{/if}
