<script lang="ts">
	import { onMount } from 'svelte';
	import { animate } from 'motion';
	import { tearDrop, circle } from '../components/TearOfAllah/constants';
	import { linear as easing } from 'svelte/easing';
	import { tweened } from 'svelte/motion';
	import { interpolateString } from 'd3-interpolate';

	let selectedPath = tearDrop;
	function select(path: string) {
		selectedPath = path;
	}
	let animated_path = tweened(tearDrop, {
		interpolate: interpolateString,
		delay: 1000,
		duration: 2000,
		easing
	});
	$: animated_path.set(selectedPath);
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
		select(circle);
	});
</script>

<div>
	<div class="box">
		<svg>
			<path d={$animated_path} fill="none" stroke="white" />
		</svg>
	</div>
</div>

<style>
	:global(html, body) {
		margin: 0;
		padding: 0;
	}
	svg {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
	div {
		height: 100vh;
		width: 100vw;
		background-color: black;
	}
	.box {
		position: relative;
		top: 10vh;
		left: 20vw;
		background-color: rgba(255, 255, 255, 0.01);
		width: 10vh;
		height: 10vh;
	}
</style>
