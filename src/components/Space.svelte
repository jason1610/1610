<script lang="ts">
	import { onMount } from 'svelte';

	let spaceBackground: HTMLDivElement;
	let scrollAmount: number = 0;
	let maxY: number;

	// function setImageHeight() {
	// 	const desiredHeight = window.innerHeight * 1.8;
	// 	spaceBackground.style.height = `${desiredHeight}px`;
	// 	maxY = desiredHeight - window.innerHeight * 0.8;
	// }

	onMount(() => {
		// setImageHeight();
		maxY = spaceBackground.clientHeight - window.innerHeight * 0.8;
		window.addEventListener('wheel', handleScroll, { passive: false });
		console.log(maxY);
		return () => {
			window.removeEventListener('wheel', handleScroll);
		};
	});

	function handleScroll(event: WheelEvent) {
		if (scrollAmount < maxY || (window.scrollY === 0 && event.deltaY < 0)) {
			event.preventDefault();
			scrollAmount += event.deltaY;
			if (scrollAmount < 0) {
				scrollAmount = 0;
			} else if (scrollAmount > maxY) {
				scrollAmount = maxY;
			}
			spaceBackground.style.transform = `translateY(-${scrollAmount}px)`;
		}
	}
</script>

<div class="space-container">
	<div class="space-background" bind:this={spaceBackground} />
</div>

<style>
	.space-container {
		position: relative;
		overflow: hidden;
		height: 80vh;
		border-radius: 0 0 30px 30px;
	}

	.space-background {
		position: absolute;
		width: 100%;
		height: 180%;
		background-image: url('../assets/space-background.png');
		background-size: cover;
		background-position: bottom;
		will-change: transform;
		transition: transform 0.2s ease;
	}
</style>
