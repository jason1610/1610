<script lang="ts">
	import Header from '../components/Header.svelte';
</script>

<Header />
<main>
	<slot />
</main>

<style>
	@font-face {
		font-family: 'Lavoir';
		src: url('../fonts/Lavoir.otf');
	}
	:global(header) {
		margin: 0;
		padding: 0;
	}

	:global(body) {
		margin: 0;
		padding: 0;
	}

	:global(html) {
		color-scheme: dark;
	}

	:global(root) {
		--title-color-primary: #fff;
		--title-color-secondary: #0a7eff;

		--text-color-primary: #fff;
		--text-color-secondary: #b3b7b9;

		--link-color-primary: #608eea;

		--message-bubble-background-gradient: linear-gradient(90deg, #0a85ff 0%, #0a7eff 100%);
		--message-bubble-background-flat: #0a7eff;

		--background-color-primary: #000000;
		--background-color-secondary: #ffffff;
		--background-color-tertiary: #050811;

		--stroke-color-primary: #263b5a;
	}
</style>
