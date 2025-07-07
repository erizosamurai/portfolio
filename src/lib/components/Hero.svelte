<script>
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
<div class="flex flex-col md:flex-row items-start justify-center min-h-screen pt-20 px-6 lg:px-24 gap-12">
  <!-- Avatar -->
  <div class="flex-shrink-0">
    <img src={avatarSrc} alt="{alias} Samurai" class="w-40 h-40 rounded-full object-cover" />
  </div>

  <!-- Right Column: Text + Arsenal + Experience -->
  <div class="w-full max-w-2xl flex flex-col gap-10">
    <!-- Intro Text -->
    <div>
     <div class="text-[32px] font-bold text-white">Hey There!</div>
    <div class="mt-4 text-[32px] font-bold text-white">
    I am <span class="text-[#008170]">{name}</span> aka <span class="text-[#008170]">{alias}</span>
    </div>

      <p class="mt-6 text-[16px] text-white leading-relaxed">
        Part Time researcher and a full-time overthinker. I spend most of my time learning about intriguing problems and reading related materials. I enjoy tackling machine learning problems and often find myself arguing with my code. I believe that the best ideas emerge from a mix of chaos and sleepless nights spent spiraling into overengineering simple problems. Currently, I am learning CUDA programming, Haskell, Rust, Go and building <a href="https://github.com/cogatimus">Cogatimus</a>, an open-source organization focused on creating a collection of useful and fascinating open-source tools.
      </p>
    </div>

    <!-- Techstack Section -->
    <div class="mt-1 flex flex-col items-start">
      <div class="text-[32px] font-bold text-white">My Arsenal</div>
      <div class="mt-4 flex flex-wrap gap-3">
        {#each icons as tech}
          <div
            class="w-9 h-9 border-dashed border-[#005B41] border-[1.5px] rounded-md flex items-center justify-center hover:scale-110 transition-transform duration-200"
            title={tech.name}
          >
            <Icon icon={tech.icon} width="29" height="29" />
          </div>
        {/each}
      </div>
    </div>

    <!-- Experience Section -->
    <div class="mt-1">
      <div class="text-[32px] font-bold text-white">Experience</div>

      <div class="mt-5 border-[1.5px] border-dashed border-[#005B41] rounded-xl p-6 text-white">
        <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-2">
          <div class="text-[16px] font-bold">
            Indian National Center for Ocean Information Services<br />
            <span class="font-bold">(INCOIS)</span>
          </div>
          <div class="italic text-sm md:text-base text-right text-gray-300">
            JUNE–AUGUST 2024
          </div>
        </div>

        <p class="text-[14px] leading-relaxed text-gray-200">
          Worked with geospatial data from the CYGNSS satellite and visualized the microplastics
          concentration in the Indian Ocean for the months of January–December 2023, and worked on
          building a predictive model for predicting the microplastics concentration for January 2024.
        </p>
      </div>
    </div>
  </div>
</div>
