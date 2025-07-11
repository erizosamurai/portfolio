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

  let hoveredTech = null;

  const toggleTech = (name) => {
    hoveredTech = hoveredTech === name ? null : name;
  };
</script>

<!-- Hero Section -->
 <!-- <div class="md:pt-10"></div> -->
<div class="flex flex-col md:flex-row items-start justify-center min-h-screen pt-20 px-6 lg:pt-15 lg:px-24 gap-12">
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
      <div class="text-[24px] sm:text-[30px] lg:text-[36px] font-bold text-[#F5F7FA]">
        Hi, <span class="text-[#00CFFF]">{name}</span> aka <span class="text-[#00CFFF]">{alias}</span> here
      </div>
      <p class="mt-4 lg:mt-6 text-[16px] sm:text-[18px] text-[#F5F7FA] leading-relaxed">
        I like reading research papers and building cool stuff.
      </p>
      <p class="mt-4 lg:mt-6 text-[16px] sm:text-[18px] text-[#F5F7FA] leading-relaxed">
        I'm mostly into Natural Language and Vision.
      </p>
      <p class="mt-4 lg:mt-6 text-[16px] sm:text-[18px] text-[#F5F7FA] leading-relaxed">
        I'm interested in photography, technology, deepscience, sports and gaming.
      </p>
    </div>
     <!-- Techstack -->
    <div in:fly={{ y: 40, delay: 200, duration: 1500 }}>
    <div class="text-[24px] sm:text-[30px] font-bold text-[#F5F7FA] mt-6">My Arsenal</div>
    <div class="mt-4 lg:mt-6 flex flex-wrap gap-3">
    {#each icons as tech (tech.name)}
      <div
        class="flex items-center gap-2 px-3 py-2 border-dashed border-[#1E88E5] border-[1.5px] rounded-md hover:scale-105 transition-transform duration-200"
        title={tech.name}
      >
        <Icon icon={tech.icon} width="24" height="24" class="sm:w-[26px] sm:h-[26px]" />
        <span class="text-sm sm:text-base text-[#F5F7FA]">{tech.name}</span>
      </div>
    {/each}
  </div>
  </div>

<!-- Experience Section -->
    <div in:fly={{ y: 40, delay: 300, duration: 1500 }}>
      <div class="text-[24px] sm:text-[30px] font-bold text-[#F5F7FA] mt-6 lg:mt-8">Experience</div>

      <div class="mt-4 lg:mt-8 border-[1.5px] border-dashed border-[#1E88E5] rounded-xl p-4 sm:p-6 text-[#F5F7FA]">
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 sm:gap-4 mb-3">
          <div class="text-[16px] sm:text-[18px] font-bold">
            Indian National Center for Ocean Information Services
          </div>
          <div class="italic text-[14px] sm:text-[15px] text-gray-300 text-right">
            JUNE–AUGUST 2024
          </div>
        </div>
        <p class="text-[14px] sm:text-[15px] leading-relaxed text-gray-200">
          Worked with geospatial data from the CYGNSS satellite and visualized the microplastics
          concentration in the Indian Ocean for the months of January–December 2023, and worked on
          building a predictive model for January 2024.
        </p>
      </div>
    </div>
  </div>
</div>
