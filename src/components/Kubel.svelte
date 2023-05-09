<script lang="ts">
	import KubelLogo from '../assets/kubel-logo.svg';
</script>

<div class="card">
	<div class="top-group">
		<div class="title">
			<div class="logo">
				<img src={KubelLogo} alt="Paint Brush Icon" />
			</div>
			<h2>Kubel.io</h2>
		</div>
		<h3>
			<span style="color: #30A8FF">Svelte</span> -
			<span style="color: #FE9A00">NodeJS</span> -
			<span style="color: #9A99FF">MongoDB</span> -
			<span style=" color: #F24E1E">Figma</span>
		</h3>
	</div>
	<p>
		Starting off in crowdsourced contests, I evolved into working freelance and under contracts. My
		works include: book covers, web UIs, logos & brand identities, animated videos, 2d asset packs
		and banners.
	</p>

	<a href="">Learn More ></a>
</div>

<style>
	.card {
		width: 400px;
		max-width: 90vw;
		background-color: var(--card-background-color-primary);
		outline: 1.5px solid var(--card-stroke-color-primary);
		border-radius: 10px;
		padding: 30px;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		gap: 20px;
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
	}

	.title .logo {
		line-height: 0;
		position: relative;
		z-index: 1;
	}

	.title .logo::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 80%;
		height: 80%;
		background-image: linear-gradient(to bottom right, blue, red, yellow, white);
		filter: blur(15px);
		z-index: -1;
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
