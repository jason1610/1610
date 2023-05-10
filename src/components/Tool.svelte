<script lang="ts">
	export let img: string;
	export let caption: string;
	export let color: string;

	import { fade } from 'svelte/transition';

	let isHovered: boolean = false;

	const getTextColor = (hexColor: string) => {
		const r = parseInt(hexColor.slice(1, 3), 16);
		const g = parseInt(hexColor.slice(3, 5), 16);
		const b = parseInt(hexColor.slice(5, 7), 16);
		const luminance = (0.299 * r + 0.587 * g + 0.114 * b) / 255;
		const color: string = luminance > 0.5 ? 'black' : 'white';
		return color;
	};

	const textColor: string = getTextColor(color);
	const handleMouseEnter = () => {
		isHovered = true;
	};
	const handleMouseLeave = () => {
		isHovered = false;
	};
</script>

<div class="container" on:mouseenter={handleMouseEnter} on:mouseleave={handleMouseLeave}>
	<img class="logo" src={img} alt="" />
	{#if isHovered}
		<div class="speech-bubble" style="background-color: {color};">
			<p style={`color:${textColor}`}>
				{caption}
			</p>
		</div>
	{/if}
	{#if isHovered}
		<img class="shadow" src={img} alt="" transition:fade={{ duration: 300 }} />
	{/if}
</div>

<style>
	.container {
		position: relative;
		width: 100px;
		height: 100px;
	}

	.logo {
		width: 100%;
		height: 100%;
		object-fit: contain;
		transition: filter 0.2s ease-in-out;
	}

	.shadow {
		width: 100%;
		height: 100%;
		position: absolute;
		top: 0%;
		object-fit: contain;
		left: 0%;
		filter: blur(10px) brightness(1.2);
		z-index: -1;
		/* opacity: 0; */
	}

	.speech-bubble {
		position: absolute;
		top: -50px;
		left: 50%;
		transform: translateX(-50%);
		padding: 8px;
		box-sizing: border-box;
		background-color: rgb(11, 10, 10);
		/* border: 1px solid black; */
		border-radius: 8px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
		text-align: center;
		animation: spawn 0.2s ease-in-out forwards;
	}

	@keyframes spawn {
		0% {
			transform: translate(-50%, 20px);
		}
		100% {
			transform: translate(-50%, 0px);
		}
	}

	.speech-bubble p {
		color: black;
		text-rendering: geometricPrecision;
	}
</style>
