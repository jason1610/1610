<script lang="ts">
	import { onMount } from 'svelte';
	import GraphicDesign from './GraphicDesignCard.svelte';
	import Kubel from './KubelCard.svelte';
	import Ideas from './IdeasCard.svelte';
	import Computers from './ComputersCard.svelte';
	import StarsBackground from '../../assets/images/stars-background.png';
	import All2 from './All2D.svelte';
</script>

<div class="white-transition" />
<div class="container">
	<h2>My Projects</h2>
	<div class="projects">
		<GraphicDesign />
		<Kubel />
		<Computers />
		<All2 />
		<Ideas />
	</div>
	<img class="background" src={StarsBackground} alt="" />
</div>

<style>
	.container {
		padding-top: 20lvh;
		padding-left: 20px;
		padding-right: 20px;
		position: relative;
		display: flex;
		flex-direction: column;
		position: relative;
		align-items: center;
		margin-top: -30px;
		/* z-index: 1; */
	}

	.white-transition {
		width: 100%;
		height: 30px;
		box-shadow: 0 -30px 0 30px white;
		border-radius: 30px 30px 0 0;
	}

	.background {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		min-height: 100%;
		object-fit: cover;
		z-index: -1;
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
</style>
