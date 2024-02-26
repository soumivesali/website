<script lang="ts">
	import { onMount } from 'svelte';
	import { animate } from 'motion';
	import TearOfAllah from '../components/TearOfAllah/TearOfAllah.svelte';
	onMount(() => {
		animate(
			'.box',
			{ position: 'relative', top: '40vh', left: '20vw' },
			{
				duration: 5,
				easing: 'ease-in-out',
				direction: 'alternate'
			}
		);
	});
</script>

<div>
	<TearOfAllah />
</div>

<style>
	:global(html, body) {
		margin: 0;
		padding: 0;
	}
	div {
		height: 100vh;
		width: 100vw;
		background-color: black;
	}
</style>
