<script lang="ts">
	import Typescript from '../../assets/logos/typescript.png';
	import React from '../../assets/logos/react.png';
	import Node from '../../assets/logos/nodejs.png';
	import GitHub from '../../assets/logos/github.png';
	import MongoDB from '../../assets/logos/mongodb.svg';
	import Vite from '../../assets/logos/vite.png';
	import Svelte from '../../assets/logos/svelte.png';
	import Pixijs from '../../assets/logos/pixijs.svg';
	import Docker from '../../assets/logos/docker.png';
	import Tauri from '../../assets/logos/tauri.svg';
	import Rust from '../../assets/logos/rust.png';
	import Tool from './Tool.svelte';
</script>

<div class="container">
	<div>
		<h2>My Toolkit</h2>
		<div class="wrapper">
			<Tool img={Typescript} caption="TypeScript" color="#2d79c7" />
			<Tool img={React} caption="React" color="#61dbfb" />
			<Tool img={Svelte} caption="SvelteKit 🤍" color="#ff3c00" />
			<Tool img={Node} caption="Nodejs" color="#539e43" />
			<Tool img={MongoDB} caption="MongoDB" color="#13aa52" />
			<Tool img={GitHub} caption="GitHub" color="#ffffff" />
			<Tool img={Vite} caption="Vite" color="#758fff" />
			<Tool img={Docker} caption="Docker" color="#2496ed" />
			<Tool img={Pixijs} caption="Pixijs" color="#e72264" />
		</div>
	</div>
	<div>
		<h2>Learning...</h2>
		<div class="wrapper">
			<Tool img={Tauri} caption="Tauri" color="#ffc131" />
			<Tool img={Rust} caption="Rust" color="#90522d" />
		</div>
	</div>
</div>

<style>
	.container {
		padding-top: 20lvh;
		padding-left: 20px;
		padding-right: 20px;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 20lvh;
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
		width: 600px;
		flex-wrap: wrap;
	}
</style>
