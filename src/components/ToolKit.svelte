<script lang="ts">
	import typescript from '../assets/typescript-logo.png';
	import react from '../assets/toolkit/react.png';
	import node from '../assets/toolkit/nodejs.png';
	import github from '../assets/toolkit/github.png';
	import mongodb from '../assets/toolkit/mongodb.svg';
	import vite from '../assets/toolkit/vite.png';
	import svelte from '../assets/toolkit/svelte.png';

	import Tool from './Tool.svelte';
</script>

<div class="container">
	<h2>My Toolkit</h2>
	<div class="wrapper">
		<Tool img={typescript} caption="TypeScript" color="#2d79c7" />
		<Tool img={react} caption="React" color="#61dbfb" />
		<Tool img={svelte} caption="SvelteKit 🤍" color="#ff3c00" />
		<Tool img={node} caption="Nodejs" color="#539e43" />
		<Tool img={mongodb} caption="MongoDB" color="#13aa52" />
		<Tool img={github} caption="GitHub" color="#ffffff" />
		<Tool img={vite} caption="Vite" color="#758fff" />
	</div>
</div>

<style>
	.container {
		padding-top: 20vh;
		padding-top: 20vhl;
		/* padding-bottom: 20vh; */
		/* padding-bottom: 20vhl; */
		padding-left: 20px;
		padding-right: 20px;
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

	.wrapper {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		gap: 50px;
		max-width: 90vw;
		width: 900px;
		flex-wrap: wrap;
	}
</style>
