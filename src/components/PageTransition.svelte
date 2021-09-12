<script>
	import { fly } from 'svelte/transition';
	export let refresh = '';
</script>

{#key refresh}
	<div
		class="transition-wrapper"
		in:fly={{ x: 50, duration: 750, delay: 750 }}
		out:fly={{ x: -50, duration: 750 }}
	>
		<slot />
	</div>
{/key}

<style>
	.transition-wrapper {
		grid-column: 1/2;
		grid-row: 1/2;
	}
</style>
