<script lang="ts">
	import { onMount } from 'svelte';
	import { animate } from 'motion';

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
	<div class="box"></div>
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
	.box {
		position: relative;
		top: 0vh;
		left: 20vw;
		background-color: red;
		width: 10vh;
		height: 10vh;
	}
</style>
