<script lang="ts">
	import { onMount } from 'svelte';

	let spaceBackground: HTMLDivElement;
	let scrollAmount: number = 0;
	let maxY: number;
	let snapToHeader: boolean = false;

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

	const handleScroll = () => {
		if (window.scrollY >= window.innerHeight * 0.8 - 70) {
			snapToHeader = true;
		} else {
			snapToHeader = false;
		}
	};

	onMount(() => {
		window.addEventListener('wheel', handleWheelScroll, { passive: false });
		window.addEventListener('scroll', handleScroll, { passive: false });
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
		};
	});
</script>

<div class={`space-container ${snapToHeader ? 'snap-to-header' : ''}`}>
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

	.snap-to-header {
		border-radius: 0;
	}
</style>
