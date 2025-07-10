<script>
  import { fly } from 'svelte/transition';
  import Icon from "@iconify/svelte";

  export let name = "Adhit";
  export let alias = "Erizo";
  export let avatarSrc = "/erizosamurai.png";

  const icons = [
    { name: "Python", icon: "material-icon-theme:python" },
    { name: "C++", icon: "vscode-icons:file-type-cpp3" },
    { name: "Go", icon: "material-icon-theme:go" },
    { name: "Rust", icon: "material-icon-theme:rust" },
    { name: "Haskell", icon: "devicon:haskell" },
    { name: "PyTorch", icon: "material-icon-theme:pytorch" },
    { name: "NumPy", icon: "vscode-icons:file-type-numpy" },
    { name: "Pandas", icon: "devicon:pandas" },
    { name: "Transformers", icon: "noto-v1:hugging-face" },
    { name: "CUDA", icon: "material-icon-theme:cuda" },
    { name: "HTML", icon: "material-icon-theme:html" },
    { name: "CSS", icon: "skill-icons:css" },
    { name: "JavaScript", icon: "vscode-icons:file-type-js-official" },
    { name: "Svelte", icon: "devicon:svelte" }
  ];
</script>

<!-- Hero Section -->
 <div class="pt-10"></div>
<div class="flex flex-col md:flex-row items-start justify-center min-h-screen pt-20 px-6 lg:pt-36 lg:px-24 gap-12">
  <!-- Avatar -->
  <div class="flex-shrink-0" in:fly={{ x: -50, duration: 1000 }}>
    <img
      src={avatarSrc}
      alt="{alias} Samurai"
      class="w-32 h-32 sm:w-40 sm:h-40 rounded-full object-cover aspect-square"
    />
  </div>

  <!-- Right Column -->
  <div class="w-full max-w-3xl flex flex-col gap-y-8">

    <!-- Intro Text -->
    <div in:fly={{ x: 50, delay: 100, duration: 1500 }}>
      <div class="text-2xl sm:text-3xl lg:text-[36px] font-bold text-white">
        Hi, <span class="text-[#008170]">{name}</span> aka <span class="text-[#008170]">{alias}</span> here
      </div>
      <p class="mt-4 lg:mt-6 text-base sm:text-lg text-white leading-relaxed">
        I like reading research papers and building cool stuff.
      </p>
      <p class="mt-4 lg:mt-6  text-base sm:text-lg text-white leading-relaxed">
        I'm mostly into Natural Language and Vision.
      </p>
      <p class="mt-4 lg:mt-6  text-base sm:text-lg text-white leading-relaxed">
        I'm interested in photography, technology, deepscience, sports and gaming.
      </p>
    </div>

    <!-- Techstack Section -->
    <div in:fly={{ y: 40, delay: 200, duration: 1500 }}>
      <div class="text-2xl sm:text-3xl font-bold text-white mt-6">My Arsenal</div>
      <div class="mt-4 lg:mt-6 flex flex-wrap gap-3">
        {#each icons as tech (tech.name)}
          <div
            class="w-8 h-8 sm:w-9 sm:h-9 border-dashed border-[#005B41] border-[1.5px] rounded-md flex items-center justify-center hover:scale-110 transition-transform duration-200"
            title={tech.name}
          >
            <Icon icon={tech.icon} width="26" height="26" class="sm:w-[29px] sm:h-[29px]" />
          </div>
        {/each}
      </div>
    </div>

    <!-- Experience Section -->
    <div in:fly={{ y: 40, delay: 300, duration: 1500 }}>
      <div class="text-2xl sm:text-3xl font-bold text-white mt-6 lg:mt-8 ">Experience</div>

      <div class="mt-4 lg:mt-8 border-[1.5px] border-dashed border-[#005B41] rounded-xl p-4 sm:p-6 text-white">
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 sm:gap-4 mb-3">
          <div class="text-base sm:text-lg font-bold">
            Indian National Center for Ocean Information Services
          </div>
          <div class="italic text-sm sm:text-base text-gray-300 text-right">
            JUNE–AUGUST 2024
          </div>
        </div>
        <p class="text-sm sm:text-[14px] leading-relaxed text-gray-200">
          Worked with geospatial data from the CYGNSS satellite and visualized the microplastics
          concentration in the Indian Ocean for the months of January–December 2023, and worked on
          building a predictive model for January 2024.
        </p>
      </div>
    </div>
  </div>
</div>
