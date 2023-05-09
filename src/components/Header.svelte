<script lang="ts">
	import { snapToHeader } from '../stores/global';
	// style={`${$snapToHeader ? 'backdrop-filter: blur(5px);' : ''}`}
</script>

<header>
	<h1>1610</h1>
</header>

<style>
	header {
		position: fixed;
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

	h1 {
		font-family: 'Lavoir';
		transition: color 0.2s ease;
		text-shadow: 0 0 3px rgba(0, 0, 0, 0.5);
	}
</style>
