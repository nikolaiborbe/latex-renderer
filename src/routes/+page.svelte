<script lang="ts">
	import Credits from './../components/Credits.svelte';
	import Latex from '../components/Latex.svelte';
	import CheatSheet from '../components/CheatSheet.svelte';
	import domtoimage from 'dom-to-image';

	let math = '';
	let formulaContainer: HTMLElement;
	let copyButtonText = 'Copy';

	// Controls whether the save options dropdown is shown
	let showSaveOptions = false;

	// Reference to the menu container for outside click detection
	let menuContainer: HTMLElement;

	// Global click handler to close menu if clicking outside
	function handleClickOutside(event: MouseEvent) {
		if (showSaveOptions && menuContainer && !menuContainer.contains(event.target as Node)) {
			showSaveOptions = false;
		}
	}

	function toggleSaveOptions() {
		showSaveOptions = !showSaveOptions;
	}

	// Generic function to save the image. For transparent, we simply omit the backgroundColor style.
	function saveImageOption(bgColor: string, filename: string) {
		const scale = 2;
		const width = formulaContainer.offsetWidth * scale;
		const height = formulaContainer.offsetHeight * scale;
		// If bgColor is 'transparent', don't include backgroundColor property.
		const style =
			bgColor !== 'transparent'
				? {
						transform: `scale(${scale})`,
						transformOrigin: 'top left',
						backgroundColor: bgColor
					}
				: {
						transform: `scale(${scale})`,
						transformOrigin: 'top left'
					};

		domtoimage
			.toPng(formulaContainer, {
				width,
				height,
				style
			})
			.then((dataUrl) => {
				const link = document.createElement('a');
				link.download = filename;
				link.href = dataUrl;
				link.click();
				showSaveOptions = false;
			})
			.catch((error) => {
				console.error('Error generating image:', error);
				showSaveOptions = false;
			});
	}

	function copyText() {
		navigator.clipboard.writeText(math);
		copyButtonText = 'Copied!';
		setTimeout(() => {
			copyButtonText = 'Copy';
		}, 2000);
	}
</script>

<!-- Global listener for clicks -->
<svelte:window on:click={handleClickOutside} />

<div class="flex h-screen flex-col px-4 items-center justify-start">
	<div class="pt-10 md:pt-20 lg:pt-72">
		{#if !math}
			<div class="h-fit w-fit px-4 py-2">
				<Latex math={'f(x) = ...'} />
			</div>
		{:else}
			<div class="h-fit w-fit px-4 py-2" bind:this={formulaContainer}>
				<Latex {math} />
			</div>
		{/if}
	</div>
	<div class="mt-10">
		<textarea
			class="h-72 w-90 md:w-[35rem] rounded-lg border border-gray-300 p-4 shadow-md focus:ring-2 focus:ring-blue-500 focus:outline-none"
			placeholder="Write your latex here..."
			bind:value={math}
		></textarea>
		<div class="flex justify-between gap-4 pt-2">
			<button
				class="w-full cursor-pointer rounded-lg border-2 bg-white p-2 shadow-md transition hover:shadow-none"
				on:click={copyText}>{copyButtonText}</button>

			<div class="relative w-full" bind:this={menuContainer}>
				<button
					class="w-full cursor-pointer rounded-lg border-2 bg-white p-2 shadow-md transition hover:shadow-none"
					on:click={toggleSaveOptions}>Save</button>
				{#if showSaveOptions}
					<div class="absolute right-0 mt-2 w-full rounded-xl border border-gray-300 bg-white shadow-md">
						<button
							class="w-full cursor-pointer rounded-t-xl px-4 py-3 hover:bg-gray-200"
							on:click={() => saveImageOption('white', 'formula.png')}
						>
							Background
						</button>
						<button
							class="w-full cursor-pointer rounded-b-xl px-4 py-3 hover:bg-gray-200"
							on:click={() => saveImageOption('transparent', 'formula_transparent.png')}
						>
							Transparent
						</button>
					</div>
				{/if}
			</div>
		</div>
	</div>

	<div class="pb-40">
		<CheatSheet />
	</div>

	<div
		class="fixed bottom-0 left-1/2 mb-6 h-15 w-52 -translate-x-1/2 transform rounded-2xl border-2 bg-white shadow-md transition hover:shadow-none"
	>
		<Credits />
	</div>
</div>
