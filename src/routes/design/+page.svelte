<script lang="ts">
	import { onMount } from 'svelte';
	onMount(() => {
		setTimeout(() => {
			window.scrollTo(0, 0);
		}, 300);
	});
</script>

<div class="container">
	<p>yo</p>
</div>

<style>
	.container {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 100vw;
		height: 100vh;
		height: 100lvh;
		padding: 20px;
		box-sizing: border-box;
	}
</style>
