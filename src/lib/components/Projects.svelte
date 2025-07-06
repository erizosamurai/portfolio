<script>
	import Icon from "@iconify/svelte";

	const projects = [
		{
			name: "Phishing URL-Detection (Capstone)",
			link: "https://github.com/Rishik00/PIMP",
			content:
				"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam vitae fermentum sapien. Vestibulum interdum ipsum quis elit pellentesque porttitor. Donec tempor dolor justo, at ornare turpis viverra quis. Phasellus viverra lorem quis enim tempus",
			techstack: [
				"material-icon-theme:python",
				"noto-v1:hugging-face",
				"logos:pytorch-icon",
				"devicon:pandas",
				"vscode-icons:file-type-numpy"
			]
		},
		{
			name: "EICL (Benchmarking Tool)",
			link: "https://github.com/cogatimus/eicl",
			content:
				"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam vitae fermentum sapien. Vestibulum interdum ipsum quis elit pellentesque porttitor. Donec tempor dolor justo, at ornare turpis viverra quis. Phasellus viverra lorem quis enim tempus",
			techstack: ["material-icon-theme:go", "material-icon-theme:python"]
		},
		{
			name: "GOVim (Text Editor)",
			link: "https://github.com/erizosamurai/govim",
			content:
				"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam vitae fermentum sapien. Vestibulum interdum ipsum quis elit pellentesque porttitor. Donec tempor dolor justo, at ornare turpis viverra quis. Phasellus viverra lorem quis enim tempus",
			techstack: ["material-icon-theme:go"]
		},
		{
			name: "FDS",
			link: "https://github.com/erizosamurai/FDS",
			content:
				"A browser extension designed to help users assess the credibility and reliability of webpages they encounter while browsing the internet. The extension utilizes an XGBoost model trained on various fraudulent links to analyze various factors such as source credibility, content quality, and factual accuracy to generate a confidence score for each webpage. Developed as part of a hackathon.",
			techstack: [
				"material-icon-theme:python",
				"devicon:pandas",
				"vscode-icons:file-type-numpy",
				"material-icon-theme:html",
				"skill-icons:css",
				"vscode-icons:file-type-js-official"
			]
		}
	];
</script>

<div class="flex flex-col gap-7 mt-10">
	<div class="text-[32px] font-bold text-white">Projects</div>

	{#each projects as project}
    <div class="border-[1.5px] border-dashed border-[#005B41] rounded-xl p-6 text-white">
    <!-- Title -->
    <div class="flex items-center gap-2 text-white font-semibold text-lg mb-2">
        {project.name}
        <a href={project.link} target="_blank" rel="noopener noreferrer">
        <Icon icon="jam:github" width="24" height="24" class="text-[#005B41]" />
        </a>
    </div>

    <!-- Tech Stack -->
    <div class="flex gap-2 flex-wrap mb-2">
        {#each project.techstack as tech}
        <div class="w-[27px] h-[27px] border border-dashed border-[#005B41] rounded-md flex items-center justify-center">
            <Icon icon={tech} width="22.37" height="22.37" />
        </div>
        {/each}
    </div>

    <!-- Description -->
    <p class="text-sm text-white leading-relaxed">{project.content}</p>
    </div>
	{/each}
</div>