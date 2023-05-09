<script lang="ts">
	export let scrollAmount: number;
	export let maxY: number;

	import { onMount, tick } from 'svelte';
	import TextMessage from './TextMessage.svelte';
	import Astronaut from '../assets/astronaut.png';

	const requiredText = [
		'Hi! Im a full stack developer from France 🇫🇷',
		'I farted',
		'I love to learn bla bla bla'
	];
	const randomText = ['Random message 1', 'Random message 2', 'Random message 3'];

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
		await new Promise((resolve) => setTimeout(resolve, 5000));
		const messageIndex = messages.findIndex((message) => message.key === key);
		messages[messageIndex].isTyping = false;

		await new Promise((resolve) => setTimeout(resolve, 10000));
		messages.pop();
		await new Promise((resolve) => setTimeout(resolve, 200));
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
	}

	.message-container {
		width: 100%;
		min-width: 50%;
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: flex-start;
	}

	img {
		width: 125px;
		max-width: 40vw;
		animation: hover 20s infinite;
	}

	@keyframes hover {
		0% {
			transform: rotate(-5deg) scale(1);
		}
		50% {
			transform: rotate(5deg) scale(0.9);
		}
		100% {
			transform: rotate(-5deg) scale(1);
		}
	}
</style>
