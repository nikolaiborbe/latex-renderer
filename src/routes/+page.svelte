<script lang="ts">
	import Latex from '../components/Latex.svelte';

	let math = $state('');
</script>

<div class="flex h-screen flex-col items-center justify-start">
	{#if math}
		<div class="pt-10 md:pt-20 lg:pt-72">
			<Latex {math} />
		</div>
	{:else}
		<div class="pt-10 md:pt-20 lg:pt-72">
			<Latex math={"f(x) "} />
		</div>
	{/if}

	<div class="mt-10">
		<textarea
			class="h-72 w-96 rounded-lg border border-gray-300 p-4 shadow-md focus:ring-2 focus:ring-blue-500 focus:outline-none"
			placeholder="Write your latex here..."
			bind:value={math}
		></textarea>
	</div>
</div>
