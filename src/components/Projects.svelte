<script lang="ts">
	import { onMount } from 'svelte';
	import GraphicDesign from './GraphicDesign.svelte';
	import Kubel from './Kubel.svelte';
	import Ideas from './Ideas.svelte';
	import AbstractBackground from '../assets/images/abstract-background.png';
</script>

<div class="container">
	<h2>My Projects</h2>
	<div class="projects">
		<GraphicDesign />
		<Kubel />
		<Ideas />
	</div>
</div>

<style>
	.container {
		padding-top: 50vh;
		padding-top: 50lvh;
		padding-bottom: 20vh;
		padding-bottom: 20lvh;
		padding-left: 20px;
		padding-right: 20px;
		position: relative;
		display: flex;
		flex-direction: column;
		position: relative;
		align-items: center;
	}

	/* @keyframes spin {
		0% {
			transform: rotate(0deg) skewX(25deg);
		}
		50% {
			transform: rotate(180deg) skewX(-25deg);
		}
		100% {
			transform: rotate(360deg) skewX(25deg);
		}
	} */

	h2 {
		font-size: 100px;
		text-align: center;
		font-weight: 400;
		margin-bottom: 100px;
		background-image: linear-gradient(to top, rgba(165, 159, 197, 0.761), #ffffff);
		background-clip: text;
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
