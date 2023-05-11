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

<header class={$snapToHeader && $page.url.pathname === '/' ? 'glow' : ''}>
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
		background-image: linear-gradient(to bottom, rgba(11, 143, 209, 0.2), rgba(10, 62, 89, 0));
		background-position: 0 -70px;
		background-repeat: no-repeat;
		transition: background-position 0.5s ease-in-out;
	}

	header.glow {
		background-position: 0 0;
	}

	a {
		color: var(--text-color-primary);
		font-size: 32px;
		font-family: 'Lavoir';
		transition: color 0.2s ease;
		text-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
	}

	@media (max-width: 750px) {
		header {
			height: 50px;
			background-position: 0 -50px;
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
