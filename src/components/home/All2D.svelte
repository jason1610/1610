<script lang="ts">
</script>

<div class="card">
	<div class="top-group">
		<div class="title">
			<div class="circle">
				<p>🎨</p>
			</div>
			<h2>All2D</h2>
		</div>
		<h3>
			<span style="color: #ffc131">Tauri</span> -
			<span style="color: #ff3c00">Svelte</span> -
			<span style="color: #2d79c7">Typescript</span> -
			<span style="color: #960000">WebGL</span>
		</h3>
	</div>
	<p>
		I've always wanted to create my own design tool. I'm currently working on my first prototype
		that will combine the best of vector and raster editing. The goal is to make working in 2d a lot
		more fun, intuitive and unify the workflow.
	</p>
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

	.title .circle {
		width: 45px;
		aspect-ratio: 1;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: rgba(78, 196, 251, 0.325);
		overflow: hidden;
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
