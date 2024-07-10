<script lang="ts">
	import { circle, tearDrop, egg, bean, puddle, puddleOne, puddleTwo, puddleThree, puddleFour, puddleFive, puddleSix, line} from './constants';
	import { linear as easing } from 'svelte/easing';
	import { tweened } from 'svelte/motion';
	import { interpolateString } from 'd3-interpolate';
	import { onMount } from 'svelte';
	import { animate } from 'motion';
	import { redirect } from '@sveltejs/kit';
	import { spring } from 'svelte/motion';

	let selectedPath = tearDrop;
	function select(path: string) {
		selectedPath = path;
	}
let animated_path = tweened(tearDrop, {
		interpolate: interpolateString,
		delay: 6000,
		duration: 4000,
		easing
	});
	$: animated_path.set(selectedPath);

	const scale = 1.0;

	select(circle);
	select(egg,);
	select(bean);
	select(puddle);
	select(puddleOne);
	select(puddleTwo);
	select(puddleThree);
	select(puddleFour);
	select(puddleFive);
	select(puddleSix);
	select(line);
	 onMount(() => {
		animate(
			'.box',
			{ position: 'absolute', top: '40vh', width: '100vw' },
			{
				duration: 7,
				easing: 'ease-in-out',
				direction: 'alternate',
				
			}
		);
	});


</script>

<div class="box">
	<svg viewBox = "0 0 100 100">
		<g transform="translate(50, 50)"></g>
		<path d={$animated_path} fill="white" stroke="white" transform = "scale({scale})" />
	</svg>
</div>

<style>


	.box {
		position: relative;
		top: calc(0vh - 60px);
		left: 0;
		background-color: rgb(255, 0, 0);
		width: 100vw;
		height: 10vh;
	}

	svg {
		position: absolute;
		top: 0;
		left: -20vw;
		width: 100%;
		height: 100%;
	}

</style>

