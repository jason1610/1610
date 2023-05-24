<script lang="ts">
	import MSDOS from '../../components/past&now/MSDOS.svelte';
	import Xp from '../../components/past&now/Xp.svelte';
	import Intro from '../../components/past&now/ComputerIntro.svelte';
	import IBM from '../../components/past&now/IBM.svelte';
	import Macintosh from '../../components/past&now/Macintosh.svelte';
	import { register } from 'swiper/element/bundle';
	register();
</script>

<!-- <div class="spacer" /> -->
<div class="container">
	<swiper-container mousewheel-force-to-axis="true">
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
