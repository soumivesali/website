<script lang="ts">
	import { tearDrop, circle } from './constants';
	import { linear as easing } from 'svelte/easing';
	import { tweened } from 'svelte/motion';
	import { interpolateString } from 'd3-interpolate';
	import { onMount } from 'svelte';
	import { animate } from 'motion';

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
	select(circle);
	onMount(() => {
		animate(
			'.box',
			{ position: 'relative', top: '40vh', left: '20vw' },
			{
				duration: 7,
				easing: 'ease-in-out',
				direction: 'alternate'
			}
		);
	});
</script>

<div class="box">
	<svg>
		<path d={$animated_path} fill="white" stroke="white" />
	</svg>
</div>

<style>
	svg {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
	.box {
		position: relative;
		top: calc(0vh - 60px);
		left: 20vw;
		background-color: rgba(255, 255, 255, 0.01);
		width: 10vh;
		height: 10vh;
	}
</style>
