<script lang="ts">
	import TearOfAllah from '../components/TearOfAllah/TearOfAllah.svelte';
</script>

<svelte:head>
	<title>Nokhte</title>
</svelte:head>
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
