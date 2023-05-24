<script lang="ts">
	import { onMount } from 'svelte';
	import MSDOS from '../../components/past-future/MSDOS.svelte';
	import Xp from '../../components/past-future/Xp.svelte';
	import Intro from '../../components/past-future/ComputerIntro.svelte';
	import IBM from '../../components/past-future/IBM.svelte';
	import Macintosh from '../../components/past-future/Macintosh.svelte';
	import { register } from 'swiper/element/bundle';
	register();

	let Swiper: any;

	onMount(() => {
		Swiper.TouchEventsTarget = 'wrapper';
		// Swiper.addEventListener('touchmove', (e: TouchEvent) => {
		// 	debug = e.touches.length;
		// 	if (e.touches.length > 1) {
		// 		Swiper.allowTouchMove = false;
		// 	} else {
		// 		Swiper.TouchEventsTarget = 'container';
		// 	}
		// });
	});
</script>

<div class="container">
	<swiper-container bind:this={Swiper}>
		<swiper-slide>
			<Intro />
		</swiper-slide>
		<swiper-slide>
			<IBM />
		</swiper-slide>
		<swiper-slide>
			<MSDOS />
		</swiper-slide>
		<swiper-slide>
			<Macintosh />
		</swiper-slide>
		<swiper-slide>
			<Xp />
		</swiper-slide>
	</swiper-container>
</div>

<style>
	swiper-container {
		width: 100%;
	}

	swiper-slide {
		/* height: 1200px; */
		display: flex;
		justify-content: center;
		height: auto !important;
	}

	:global(.swiper-button-next) {
		background-color: red;
		width: 500px;
		height: 500px;
	}

	.container {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 100%;
	}
</style>
