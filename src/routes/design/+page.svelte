<script lang="ts">
	import { onMount } from 'svelte';
	import Book from '../../assets/design/book.png';
	import Magica from '../../assets/design/magica.png';
	import MrNight from '../../assets/design/mrnight.gif';
	import Portrait from '../../assets/design/portrait.jpg';
	import W117 from '../../assets/design/w117.png';
	import Victoria from '../../assets/design/victoria.png';
	import ND from '../../assets/design/nd.gif';
	import Space from '../../assets/design/space.png';
	import House from '../../assets/design/house.png';
	import SunGirl from '../../assets/design/sun-girl.png';

	onMount(() => {
		setTimeout(() => {
			if (window.scrollY > 0) window.scrollTo(0, 0);
		}, 310);
	});
</script>

<div class="container">
	<div class="info">
		<h1>My portfolio</h1>
		<p>
			I have experience in many different mediums. I have worked on projects ranging from graphic
			design to book covers. Take a look at some of my work below.
		</p>
	</div>
	<div class="portfolio">
		<img class="book" src={Book} alt="" />
		<img class="magica" src={Magica} alt="" />
		<img class="mrnight" src={MrNight} alt="" />
		<img class="portrait" src={Portrait} alt="" />
		<img class="w117" src={W117} alt="" />
		<img class="victoria" src={Victoria} alt="" />
		<img class="nd" src={ND} alt="" />
		<img class="space" src={Space} alt="" />
		<img class="house" src={House} alt="" />
		<img class="sungirl" src={SunGirl} alt="" />
	</div>
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		width: 100vw;
		gap: 50px;
		padding: 20px;
		box-sizing: border-box;
	}

	.portfolio {
		width: 800px;
		max-width: 90vw;
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 20px;
	}
	.portfolio img {
		object-fit: cover;
		border-radius: 20px;
		width: 100%;
		height: 100%;
	}

	.magica {
		grid-column: 1 / 4;
		grid-row: 1;
	}

	.mrnight {
		grid-column: 1 / 3;
		grid-row: 2;
	}

	.space {
		grid-column: 3 / 4;
		grid-row: 2;
		object-position: 70% 100%;
	}

	.book {
		grid-column: 2 / 4;
		grid-row: 3 / 5;
	}

	.house {
		grid-column: 1;
		grid-row: 3 / 5;
	}

	.nd {
		grid-column: 1;
		grid-row: 5;
	}

	.w117 {
		grid-column: 3;
		grid-row: 5;
	}

	.victoria {
		grid-column: 2;
		grid-row: 5;
	}

	.portrait {
		grid-column: 1 / 3;
		grid-row: 6/8;
	}

	.sungirl {
		grid-column: 3;
		grid-row: 6 / 7;
	}

	.info {
		font-size: 20px;
		font-weight: 400;
		color: var(--text-color-primary);
		max-width: 90vw;
		width: 800px;
	}
</style>
