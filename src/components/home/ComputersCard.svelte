<script lang="ts">
	import { goto } from '$app/navigation';

	import PaintBrushIcon from '../../assets/icons/brush.svg';
</script>

<div class="card">
	<div class="top-group">
		<div class="title">
			<div class="circle">
				<p>🖥️</p>
				<!-- <img src={PaintBrushIcon} alt="Paint Brush Icon" /> -->
			</div>
			<h2>Past-Future</h2>
		</div>
		<h3>
			<span style="color: #30A8FF">Typescript</span>
			<!-- <span style="color: #FE9A00">Illustrator</span> -
			<span style="color: #9A99FF">Premiere Pro</span> -
			<span style=" color: #F24E1E">Figma</span> -->
		</h3>
	</div>
	<p>
		Tech has moved so fast that many of us dont know how it started. Here is an interactive
		presentation on the inovation in computers. This is an ongoing project that I will be adding to.
	</p>

	<a href="/past-future">Check it out ></a>
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

	.title img {
		width: 55%;
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
