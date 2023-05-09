<script lang="ts">
	import { onMount } from 'svelte';
	import { snapToHeader } from '../stores/global';
	let spaceBackground: HTMLDivElement;
	let scrollAmount: number = 0;
	let maxY: number;
	let touchStartY: number;

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
		touchStartY = event.touches[0].clientY;
	};

	const handleScroll = () => {
		if (window.scrollY >= window.innerHeight * 0.8 - 70) {
			snapToHeader.set(true);
		} else {
			snapToHeader.set(false);
		}
	};

	onMount(() => {
		window.addEventListener('wheel', handleWheelScroll, { passive: false });
		window.addEventListener('scroll', handleScroll, { passive: false });
		window.addEventListener('touchstart', handleTouchStart, { passive: false });
		window.addEventListener('touchmove', handleTouchMove, { passive: false });
		maxY = spaceBackground.clientHeight - window.innerHeight * 0.8;
		window.addEventListener('resize', () => {
			maxY = spaceBackground.clientHeight - window.innerHeight * 0.8;
		});
		if (window.scrollY > 0) {
			scrollAmount = maxY;
			spaceBackground.style.transform = `translateY(-${scrollAmount}px)`;
		}
		return () => {
			window.removeEventListener('wheel', handleWheelScroll);
			window.removeEventListener('resize', () => {
				maxY = spaceBackground.clientHeight - window.innerHeight * 0.8;
			});
			window.removeEventListener('scroll', handleScroll);
			window.removeEventListener('touchstart', handleTouchStart);
			window.removeEventListener('touchmove', handleTouchMove);
		};
	});
</script>

<div class={`space-container ${$snapToHeader ? 'snap-to-header' : ''}`}>
	<div class="space-background" bind:this={spaceBackground} />
</div>

<style>
	.space-container {
		overflow: hidden;
		height: 80vh;
		border-radius: 0 0 30px 30px;
		position: sticky;
		top: calc(-80vh + 70px);
		transition: border-radius 0.2s ease;
		z-index: 1;
	}

	.space-background {
		position: absolute;
		width: 100%;
		height: 180%;
		background-image: url('../assets/space-background.png');
		background-size: cover;
		background-position: bottom;
		will-change: transform;
		transition: transform 0.5s ease;
	}

	.snap-to-header {
		border-radius: 0;
		box-shadow: 0 0 50px rgba(0, 0, 0, 1);
	}
</style>
