<script lang="ts">
	import KubelLogo from '../../assets/logos/kubel.svg';
</script>

<div class="card">
	<div class="top-group">
		<div class="title">
			<img src={KubelLogo} alt="Paint Brush Icon" />
			<h2>Kubel.io</h2>
		</div>
		<h3>
			<span style="color: #f73c00">Svelte</span> -
			<span style="color: #7cc327">Node.js</span> -
			<span style="color: #00ed64">MongoDB</span>
		</h3>
	</div>
	<p>
		For my first full-stack project, I created Kubel, a daily puzzle game featuring a 2D Rubik's
		cube, offering an enjoyable challenge. Competitive players can aim for top spots on the
		leaderboard.
	</p>
	<a href="https://kubel.io/" target="_blank">Check it out ></a>
</div>

<style>
	.card {
		width: 400px;
		max-width: 90vw;
		background-color: var(--card-background-color-primary);
		box-shadow: 0 0 0 1.5px var(--card-stroke-color-primary);
		border-radius: 10px;
		padding: 30px;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		gap: 20px;
		overflow: hidden;
		backdrop-filter: blur(5px);
		-webkit-backdrop-filter: blur(5px);
	}

	.top-group {
		display: flex;
		flex-direction: column;
		gap: 10px;
	}

	.title {
		display: flex;
		gap: 10px;
		align-items: center;
		font-size: 25px;
	}

	.title h2 {
		font-weight: 500;
	}

	.title img {
		width: 45px;
		aspect-ratio: 1;
		filter: drop-shadow(0px 0px 5px rgba(69, 180, 216, 0.3));
	}

	h3 {
		font-size: 12px;
		font-weight: 400;
		opacity: 0.8;
	}

	p {
		color: var(--text-color-secondary);
	}
</style>
