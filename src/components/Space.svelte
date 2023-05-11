<script lang="ts">
	import { onMount } from 'svelte';
	import { snapToHeader } from '../stores/global';
	import Astronaut from './Astronaut.svelte';
	import { fade } from 'svelte/transition';
	import Down from '../assets/icons/down.svg';

	let spaceBackground: HTMLDivElement;
	let lvhDiv: HTMLDivElement;
	let lvh: number;
	let scrollAmount: number = 0;
	let maxY: number;
	let touchStartY: number;
	let showDownArrow: boolean = false;

	const startTimer = () => {
		setTimeout(() => {
			showDownArrow = true;
		}, 5000);
	};

	const handleScroll = () => {
		if (window.scrollY >= lvh * 0.8 - 70) {
			snapToHeader.set(true);
			showDownArrow = false;
		} else {
			snapToHeader.set(false);
		}
	};

	const handleWheelScroll = (event: WheelEvent) => {
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
		handleScroll();
	};

	const handleTouchStart = (event: TouchEvent) => {
		touchStartY = event.touches[0].clientY;
	};

	const handleTouchMove = (event: TouchEvent) => {
		const deltaY = touchStartY - event.touches[0].clientY;

		if (scrollAmount < maxY || (window.scrollY === 0 && deltaY < 0)) {
			event.preventDefault();
			scrollAmount += deltaY;
			if (scrollAmount < 0) {
				scrollAmount = 0;
			} else if (scrollAmount > maxY) {
				scrollAmount = maxY;
			}
			spaceBackground.style.transform = `translateY(-${scrollAmount}px)`;
		}
		handleScroll();
		// handleResize();
		touchStartY = event.touches[0].clientY;
	};

	const handleResize = () => {
		let reachedBottom: boolean = false;
		if (scrollAmount === maxY) reachedBottom = true;

		maxY = spaceBackground.clientHeight - lvh * 0.8;
		if (scrollAmount < 0) {
			scrollAmount = 0;
		} else if (scrollAmount > maxY) {
			scrollAmount = maxY;
		}
		if (reachedBottom) scrollAmount = maxY;
		spaceBackground.style.transform = `translateY(-${scrollAmount}px)`;
		handleScroll();
	};

	onMount(() => {
		lvh = lvhDiv.clientHeight;
		maxY = spaceBackground.clientHeight - lvh * 0.8;
		if (window.scrollY > 0) {
			scrollAmount = maxY;
			spaceBackground.style.transform = `translateY(-${scrollAmount}px)`;
		} else startTimer();
		handleScroll();

		window.addEventListener('wheel', handleWheelScroll, { passive: false });
		window.addEventListener('scroll', handleScroll, { passive: false });
		window.addEventListener('touchstart', handleTouchStart, { passive: false });
		window.addEventListener('touchmove', handleTouchMove, { passive: false });
		window.addEventListener('resize', handleResize);
		return () => {
			window.removeEventListener('wheel', handleWheelScroll);
			window.removeEventListener('resize', handleResize);
			window.removeEventListener('scroll', handleScroll);
			window.removeEventListener('touchstart', handleTouchStart);
			window.removeEventListener('touchmove', handleTouchMove);
		};
	});
</script>

<div class="lvh" bind:this={lvhDiv} />
<div class="space-container">
	{#if showDownArrow}
		<img class="down" src={Down} alt="scroll" transition:fade={{ duration: 300 }} />
	{/if}
	<Astronaut {scrollAmount} {maxY} />
	<div class="space-background" bind:this={spaceBackground} />
</div>
<div class="white" />
<div class="white-transition" />

<style>
	.space-container {
		overflow: hidden;
		height: 80vh;
		height: 80lvh;
		border-radius: 0 0 30px 30px;
		position: relative;
		/* position: sticky; */
		/* top: calc(-80vh + 70px);
		top: calc(-80lvh + 70px); */
		/* transition: border-radius 0.2s ease; */
		z-index: 1;
		margin-top: -70px;
		background-color: white;
	}

	.white {
		width: 100%;
		height: calc(20vh + 30px);
		height: calc(20lvh + 30px);
		background-color: white;
		margin-top: -30px;
		top: 0;
		left: 0;
	}

	.white-transition {
		width: 100%;
		/* height: 200px; */
		height: 30px;
		box-shadow: 0 -30px 0 30px white;

		border-radius: 30px 30px 0 0;
	}

	@media (max-width: 750px) {
		.space-container {
			margin-top: -50px;
		}
	}

	.down {
		position: absolute;
		bottom: 30px;
		left: 50%;
		z-index: 1;
		transform: translate(-50%, 0);
		animation: bounce 1.5s ease-in-out infinite;
	}

	@keyframes bounce {
		0% {
			transform: translate(-50%, 0);
		}
		50% {
			transform: translate(-50%, -10px);
		}
		100% {
			transform: translate(-50%, 0);
		}
	}

	.space-background {
		position: absolute;
		width: 100%;
		height: 180%;
		background-image: url('../assets/images/space-background.png');
		background-size: cover;
		background-position: bottom;
		will-change: transform;

		transition: transform 0.5s ease;
	}

	.snap-to-header {
		border-radius: 0;
		box-shadow: 0 0 50px rgba(0, 0, 0, 1);
	}

	.lvh {
		position: absolute;
		pointer-events: none;
		height: 100vh;
		height: 100lvh;
	}
</style>
