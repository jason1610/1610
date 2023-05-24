<script lang="ts">
	import Image from './assets/pc.png';
	import Finger from './assets/pointing-emoji.png';
</script>

<div class="container">
	<div class="content">
		<!-- <img id="pointer" src={Finger} alt="" /> -->
		<img id="computer" src={Image} alt="" />
		<div class="article">
			<h1>Computers & OS</h1>
			<p>
				Computers changed the world. Take a look at some of the most iconic computers and operating
				systems.
			</p>
		</div>
	</div>
</div>

<style>
	.container {
		padding: var(--carousel-padding);
		box-sizing: border-box;
		display: flex;
		background: linear-gradient(to top, #b8b8b8 5%, white 30%, white 40%, #49869e);
		flex-direction: column;
		width: 100%;
		min-height: 100svh;
		height: 100%;
		align-items: center;
		justify-content: center;
		cursor: default;
	}
	.content {
		max-width: var(--max-content-width);
		display: grid;
		grid-template-columns: 2fr 1fr;
		/* width: 100%;
		height: 100%; */
		align-items: center;
		box-sizing: border-box;
		justify-content: center;
	}

	.article {
		width: 100%;
	}

	.article h1 {
		color: var(--text-color-tertiary);
	}
	.article p {
		color: rgb(120, 120, 120);
	}

	#pointer {
		height: 100px;

		position: absolute;
		bottom: 5px;
		left: 50%;
		transform: translate(-50%, 0);
		z-index: 2;
		animation: swipe 2s ease-in-out infinite;
	}

	@keyframes swipe {
		0% {
			rotate: 0deg;
		}
		50% {
			rotate: 10deg;
			transform: translate(-50%, 0);
		}
		100% {
			rotate: 0deg;
		}
	}

	#computer {
		width: 100%;
		height: 100%;
		max-height: 700px;
		object-fit: contain;
	}

	/* Responsive design - switch to column layout for smaller screens */
	@media (max-width: 700px) {
		.content {
			grid-template-columns: 1fr;
			grid-template-rows: 1fr 1;
		}
	}

	@media (max-width: 500px) {
		h1 {
			font-size: 40px;
			line-height: 35px;
		}
	}
</style>
