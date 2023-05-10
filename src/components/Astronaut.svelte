<script lang="ts">
	export let scrollAmount: number;
	export let maxY: number;

	import { onMount, tick } from 'svelte';
	import TextMessage from './TextMessage.svelte';
	import Astronaut from '../assets/astronaut.png';

	const monthsSince = (date: Date) => {
		const now = new Date();
		return (now.getFullYear() - date.getFullYear()) * 12 + (now.getMonth() - date.getMonth());
	};
	const start = new Date(2023, 1, 1);
	const months = monthsSince(start);

	const requiredText = [
		`Hi! I'm a full stack developer from France 😀`,
		'My projects make the world a better place',
		'Have a project in mind?'
	];
	const randomText = [
		'I farted',
		'My favororite color is 🟧',
		'Hey!',
		'Gorilla army, ATTACK! 🦍🦍🦍🦍🦍🦍🦍🦍🦍🦍',
		`I started learning full stack ${months} months ago`,
		`I have no idea how to get down from here`,
		`I'm hungry`,
		`I'm bored`,
		`Whats up?`,
		'The first-ever computer game is called Spacewar.',
		'It took less code to send a man to the Moon than to run a smartphone.',
		'USA has a literacy rate of 99%. Imagine if 99% of people could code.',
		'NASA still operates some projects on programming from the 1970’s.'
	];

	const minTypingTime: number = 1000;
	const addedTypingTime: number = 2000;
	const minMessageTime: number = 4000;
	const addedMessageTime: number = 3000;

	interface Message {
		text: string;
		key: number;
		isTyping: boolean;
	}

	let messages: Message[] = [];

	onMount(async () => {
		for (let i = 0; i < requiredText.length; i++) {
			await displayMessage(requiredText[i]);
		}
		while (true) {
			const randomIndex = Math.floor(Math.random() * randomText.length);
			await displayMessage(randomText[randomIndex]);
		}
	});

	async function displayMessage(text: string) {
		const key = Date.now();
		const message: Message = { text, key, isTyping: true };
		messages = [{ ...message }, ...messages];
		await tick();
		await new Promise((resolve) =>
			setTimeout(resolve, minTypingTime + Math.random() * addedTypingTime)
		);
		const messageIndex = messages.findIndex((message) => message.key === key);
		messages[messageIndex].isTyping = false;

		await new Promise((resolve) =>
			setTimeout(resolve, minMessageTime + Math.random() * addedMessageTime)
		);
		if (messages.length > 1) {
			messages.pop();
			messages = [...messages];
		}
		// await new Promise((resolve) => setTimeout(resolve, 1000));
	}
</script>

<div class="container" style={`top: ${(scrollAmount / maxY) * 25 + 40}%`}>
	<img src={Astronaut} alt="" />
	<div class="message-container">
		{#each messages as { text, key, isTyping } (key)}
			<TextMessage message={text} {isTyping} />
		{/each}
	</div>
</div>

<style>
	.container {
		position: absolute;
		width: 350px;
		max-width: 90vw;
		top: 50%;
		left: 50%;
		z-index: 1;
		transition: top 1.25s ease;
		transform: translate(-50%, -50%);
		display: flex;
		flex-wrap: nowrap;
		overflow-anchor: bottom;
		height: 170px;
	}

	.message-container {
		width: 100%;
		min-width: 50%;
		display: flex;
		flex-direction: column-reverse;
		gap: 5px;
		justify-content: flex-start;
		align-items: flex-start;
		position: relative;
		transform: translateY(calc(-100% + 34px));
		height: 500px;
	}

	img {
		width: 125px;
		max-width: 40vw;
		object-fit: contain;
		animation: hover 20s ease-in-out infinite;
	}

	/* img:hover {
		cursor: pointer;
	}

	img:active {
		animation-play-state: paused;
		transform: scale(1.5);
	} */

	@keyframes hover {
		0% {
			transform: rotate(-8deg) scale(1);
		}
		50% {
			transform: rotate(5deg) scale(0.9);
		}
		100% {
			transform: rotate(-8deg) scale(1);
		}
	}
</style>
