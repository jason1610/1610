<script lang="ts">
	import { onMount } from 'svelte';
	import GraphicDesign from './GraphicDesign.svelte';
	import Kubel from './Kubel.svelte';
	import Ideas from './Ideas.svelte';

	let opacity = 1;
	let transitionPoint: number;

	function handleScroll() {
		const currentScrollY = window.scrollY;
		if (currentScrollY >= 0 && currentScrollY <= transitionPoint) {
			opacity = 1 - currentScrollY / transitionPoint;
		} else {
			opacity = 0;
		}
	}

	onMount(() => {
		transitionPoint = window.innerHeight * 0.3;
		handleScroll();
		window.addEventListener('scroll', handleScroll);
		return () => {
			window.removeEventListener('scroll', handleScroll);
		};
	});
</script>

<div class="container">
	<h2>My Projects</h2>
	<div class="projects">
		<GraphicDesign />
		<Kubel />
		<Ideas />
	</div>
	<div class="background" style="opacity: {opacity};" />
</div>

<style>
	.container {
		margin-top: -40px;
		padding-top: 50vh;
		padding-top: 50lvh;
		padding-bottom: 20vh;
		padding-bottom: 20lvh;
		padding-left: 20px;
		padding-right: 20px;
		position: relative;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	h2 {
		font-size: 100px;
		text-align: center;
		font-weight: 400;
		margin-bottom: 100px;
		background-image: linear-gradient(to top, rgba(165, 159, 197, 0.761), #ffffff);
		-webkit-background-clip: text;
		color: transparent;
	}

	@media (max-width: 600px) {
		h2 {
			font-size: 75px;
		}
	}

	.projects {
		display: flex;
		justify-content: row;
		flex-wrap: wrap;
		justify-content: center;
		width: 900px;
		max-width: 90vw;
		gap: 20px;
	}
	.background {
		background-color: var(--background-color-secondary);
		position: absolute;
		height: 100%;
		width: 100%;
		top: 0;
		left: 0;
		transition: opacity 0.3s ease;
		pointer-events: none;
	}
</style>
