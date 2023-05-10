<script lang="ts">
	import Header from '../components/Header.svelte';
	import Footer from '../components/Footer.svelte';
	import { fade } from 'svelte/transition';
	import { onMount } from 'svelte';

	export let data: any;

	export let handleScroll = false;

	onMount(async () => {
		// disableScrollHandling();
	});
</script>

<Header />
{#key data.pathname}
	<main transition:fade={{ duration: 300 }}>
		<slot />
	</main>
{/key}
<Footer />

<style>
	@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap');

	@font-face {
		font-family: 'Lavoir';
		src: url('../assets/fonts/Lavoir.otf');
	}

	:global(header) {
		margin: 0;
		padding: 0;
	}

	:global(body) {
		margin: 0;
		padding: 0;
		font-family: 'Roboto', sans-serif;
		background-color: var(--background-color-primary);
	}

	:global(html) {
		scroll-behavior: smooth;
		color-scheme: dark;

		--title-color-primary: #fff;
		--title-color-secondary: #0a7eff;

		--text-color-primary: #fff;
		--text-color-secondary: #a4becb;
		--text-color-tertiary: #3d7f90;

		--link-color: #608eea;
		--link-color-hover: #0a7eff;

		--message-bubble-background-gradient: linear-gradient(90deg, #0a85ff 0%, #0a7eff 100%);
		--message-bubble-background-flat: #0a7eff;

		--background-color-primary: #050811;
		--background-color-secondary: #ffffff;

		--card-background-color-primary: #263b5a80;
		--card-stroke-color-primary: #263b5a;
	}

	:global(h1, h2, h3, p, a) {
		padding: 0;
		margin: 0;
	}

	:global(a) {
		text-decoration: none;
		color: var(--link-color);
	}

	:global(a:hover) {
		color: var(--link-color-hover);
		transition: color 0.2s ease, text-decoration 0.2s ease;
	}
</style>
