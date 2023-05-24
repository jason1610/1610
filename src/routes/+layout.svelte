<script lang="ts">
	import Header from '../components/layout/Header.svelte';
	import Footer from '../components/layout/Footer.svelte';
	import { fade } from 'svelte/transition';

	export let data: any;
</script>

<Header />
{#key data.pathname}
	<main transition:fade={{ duration: 300 }}>
		<slot />
	</main>
{/key}
<Footer />
