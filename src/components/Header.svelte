<script lang="ts">
	import { snapToHeader } from '../stores/global';
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';

	let logoLink: string = '/';
	$: {
		if ($page.url.pathname === '/') {
			logoLink = '#top';
		} else {
			logoLink = '/';
		}
	}

	function handleLogoClick(event: MouseEvent) {
		event.preventDefault();
		if (logoLink === '#top') {
			window.scrollTo(0, 0);
		} else {
			goto(logoLink);
		}
	}

	// style={`${$snapToHeader ? 'backdrop-filter: blur(5px);' : ''}`}
</script>

<header>
	<a href={logoLink} on:click={handleLogoClick}>1610</a>
</header>

<style>
	header {
		position: sticky;
		display: flex;
		height: 70px;
		width: 100vw;
		top: 0;
		align-items: center;
		padding: 20px;
		box-sizing: border-box;
		z-index: 9999;
		/* transition: background-color 0.2s ease; */
	}

	a {
		color: var(--text-color-primary);
		font-size: 32px;
		font-family: 'Lavoir';
		transition: color 0.2s ease;

		/* text-shadow: 0 0 3px rgba(0, 0, 0, 0.5); */
	}

	@media (max-width: 750px) {
		header {
			height: 50px;
		}
		a {
			font-size: 25px;
		}
	}

	a:hover {
		cursor: pointer;
		color: var(--text-color-primary);
	}
</style>
