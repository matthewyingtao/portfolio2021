<script>
	import { fly } from 'svelte/transition';
	export let refresh = '';
</script>

{#key refresh}
	<div in:fly={{ x: 50, duration: 750, delay: 800 }} out:fly={{ x: -50, duration: 750 }}>
		<slot />
	</div>
{/key}
