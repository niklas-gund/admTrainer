<script lang="ts">
	import RSC from './components/ReedSalomonTrainer.svelte'

	const moduleNames: string[] = ["RSC", "test1", "test2", "test3"]
	var selectedModule: string = "RSC"
</script>

<main class="container mx-auto">
	<h1>ADM - Trainer</h1>
	<div class="flex">
		{#each moduleNames as module, index}
		<div class="flex-initial w-32 moduleSelectorItem {selectedModule == module?"moduleSelectorSelected":""}"
		on:click="{() => selectedModule = module}">
			{module}
		</div>
		{/each}
	</div>
	<div class="spacer"/>
	{#if selectedModule == "RSC"}
	<RSC/>
	{/if}
</main>

<style lang="postcss" global>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;

	:root{
		--lightBlue: #8ecae6;
		--blue: #219ebc;
		--darkBlue: #023047;
		--yellow: #ffb703;
		--orange: #fb8500;
	}

	h1{
		color: var(--darkBlue);
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	h2{
		color: var(--darkBlue);
		text-transform: uppercase;
		font-size: 2em;
		font-weight: 500;
	}
	h3{
		color: var(--darkBlue);
		text-transform: uppercase;
		font-size: 2em;
		font-weight: 300;
	}

	.spacer{
		height: 10px;
	}

	* {
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
	}

	.moduleSelectorItem{
		background-color: var(--blue);
		margin: 0 10px 0 10px;
		padding: 5px 20px;
		border-radius: 5px;
		font-weight: 500;
	}

	.moduleSelectorSelected{
		background-color: var(--darkBlue);
		color: white;
	}

  </style>

  <!-- colors: 8ecae6 219ebc 023047 ffb703 fb8500-->