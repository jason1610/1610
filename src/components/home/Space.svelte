<script lang="ts">
	import { onMount } from 'svelte';
	import Astronaut from './Astronaut.svelte';
	// @ts-ignore
	import Matter from 'matter-js';

	let astronautElement: HTMLDivElement;
	let spaceContainerElement: HTMLDivElement;
	let spaceBackgroundElement: HTMLDivElement;
	let engine: any = Matter.Engine.create({ gravity: { x: 0, y: 0 } });
	let lvhDiv: HTMLDivElement;
	let lvh: number;
	let scrollAmount: number = 0;
	let maxY: number;

	const handleWheelScroll = (event: WheelEvent) => {
		scrollAmount += event.deltaY;
		if (scrollAmount < 0) {
			scrollAmount = 0;
		}
		spaceBackgroundElement.style.transform = `translateY(-${Math.min(scrollAmount, maxY)}px)`;
	};

	const handleResize = () => {
		let reachedBottom: boolean = false;
		if (scrollAmount === maxY) reachedBottom = true;

		maxY = spaceBackgroundElement.clientHeight - lvh * 0.8;
		if (scrollAmount < 0) {
			scrollAmount = 0;
		} else if (scrollAmount > maxY) {
			scrollAmount = maxY;
		}
		if (reachedBottom) scrollAmount = maxY;
		spaceBackgroundElement.style.transform = `translateY(-${scrollAmount}px)`;
	};

	let threshold = 150;

	const applyForce = (astronaut: any, mouse: any) => {
		if (!astronautElement) return;
		let distance = Matter.Vector.magnitude(Matter.Vector.sub(mouse.position, astronaut.position));
		if (distance < threshold) {
			let direction = Matter.Vector.normalise(
				Matter.Vector.sub(astronaut.position, mouse.position)
			);
			let force = Math.min(0.001, 0.02 / (distance + 0.001));
			// let force = 0.001;
			Matter.Body.applyForce(astronaut, astronaut.position, Matter.Vector.mult(direction, force));
		}

		astronautElement.style.left = `${astronaut.position.x}px`;
		astronautElement.style.top = `${astronaut.position.y}px`;
		astronautElement.style.transform = `rotate(${astronaut.angle}rad)`;
	};

	onMount(() => {
		lvh = lvhDiv.clientHeight;
		maxY = spaceBackgroundElement.clientHeight - lvh * 0.8;
		if (window.scrollY > 0) {
			scrollAmount = maxY;
			spaceBackgroundElement.style.transform = `translateY(-${scrollAmount}px)`;
		}

		let astronaut = Matter.Bodies.rectangle(
			lvhDiv.clientWidth / 2 - astronautElement.clientWidth / 2,
			lvhDiv.clientHeight / 2,
			62.5,
			astronautElement.clientHeight,
			{
				restitution: 0.8,
				friction: 0,
				frictionAir: 0.001
			}
		);
		handleWheelScroll({ deltaY: 0 } as WheelEvent);
		let mouse = Matter.Bodies.circle(lvhDiv.clientWidth, 0, 10, { isSensor: true });
		let offset = 5;
		let options = { isStatic: true };
		let width = spaceContainerElement.offsetWidth;
		let height = spaceContainerElement.offsetHeight;
		let walls = [
			Matter.Bodies.rectangle(width / 2, -offset, width + 2 * offset, 50, options), // top
			Matter.Bodies.rectangle(width / 2, height + offset, width + 2 * offset, 50, options), // bottom
			Matter.Bodies.rectangle(width + offset, height / 2, 50, height + 2 * offset, options), // right
			Matter.Bodies.rectangle(-offset, height / 2, 50, height + 2 * offset, options) // left
		];
		Matter.World.add(engine.world, [astronaut, ...walls]);
		Matter.Runner.run(engine);

		Matter.Events.on(engine, 'afterUpdate', function () {
			applyForce(astronaut, mouse);
		});
		astronautElement.style.opacity = '1';

		window.addEventListener('mousemove', function (event) {
			Matter.Body.setPosition(mouse, { x: event.clientX, y: window.scrollY + event.clientY });
		});
		window.addEventListener('wheel', handleWheelScroll, { passive: false });
		window.addEventListener('resize', handleResize);
		return () => {
			Matter.Runner.stop(engine);
			Matter.Events.off(engine, 'afterUpdate', function () {});
			window.removeEventListener('wheel', handleWheelScroll);
			window.removeEventListener('resize', handleResize);
			window.removeEventListener('mousemove', () => {});
		};
	});
</script>

<div class="lvh" bind:this={lvhDiv} />
<div class="space-container" bind:this={spaceContainerElement}>
	<div bind:this={astronautElement} class="astronaut">
		<Astronaut />
	</div>
	<div class="space-background" bind:this={spaceBackgroundElement} />
</div>
<div class="white" />

<style>
	.astronaut {
		position: absolute;
		left: 500px;
		top: 500px;
		z-index: 100;
		pointer-events: none;
		z-index: 100;
		opacity: 0;
		transition: opacity 0.5s ease;
	}

	.space-container {
		overflow: hidden;
		height: 80lvh;
		border-radius: 0 0 30px 30px;
		position: relative;
		/* position: sticky; */
		/* top: calc(-80vh + 70px);
		top: calc(-80lvh + 70px); */
		/* transition: border-radius 0.2s ease; */
		z-index: 1;
		background-color: white;
	}

	.white {
		width: 100%;
		height: calc(20vh + 30px);
		height: calc(20lvh + 30px);
		background-color: white;
		margin-top: -30px;
		top: 0;
		left: 0;
	}

	@media (max-width: 750px) {
		.space-container {
			margin-top: -50px;
		}
	}

	@keyframes bounce {
		0% {
			transform: translate(-50%, 0);
		}
		50% {
			transform: translate(-50%, -10px);
		}
		100% {
			transform: translate(-50%, 0);
		}
	}

	.space-background {
		position: absolute;
		width: 100%;
		height: 180%;
		background-image: url('../../assets/images/space-background.png');
		background-size: cover;
		background-position: bottom;
		will-change: transform;
		transform: translateY(-30%);
		transition: transform 0.5s ease;
	}

	.lvh {
		position: absolute;
		pointer-events: none;
		height: 100vh;
		height: 100lvh;
		width: 100%;
	}
</style>
