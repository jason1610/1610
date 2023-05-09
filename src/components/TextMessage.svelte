<script lang="ts">
	import { fade } from 'svelte/transition';

	export let message: string;
	export let isTyping: boolean = true;
	console.log(isTyping);
</script>

<div class={`message-bubble ${isTyping ? 'typing' : ''}`} in:fade={{ duration: 300 }}>
	<div class="content">
		{#if isTyping}
			<div class="typing-indicator">
				<span class="dot" />
				<span class="dot" />
				<span class="dot" />
			</div>
		{:else}
			<p>
				{message}
			</p>
		{/if}
	</div>
</div>

<style>
	.message-bubble {
		display: grid;
		grid-template-rows: 1fr;
		min-width: 50px;
		min-height: 20px;
		background-color: var(--message-bubble-background-flat);
		background: var(--message-bubble-background-gradient);
		border-radius: 10px 10px 10px 0;
		overflow: hidden;
		padding: 7px;
		transition: grid-template-columns 0.5s ease, grid-template-rows 0.5s ease,
			border-radius 0.5s ease;
	}
	.typing {
		display: flex;
		justify-content: center;
		align-items: center;
		grid-template-rows: 0fr;
		border-radius: 20px;
	}

	.content {
		/* overflow: hidden; */
		display: flex;
		align-items: center;
		justify-self: center;
	}

	.typing-indicator {
		display: flex;
		justify-content: center;
	}

	.dot {
		background-color: #ffffff;
		border-radius: 50%;
		width: 6px;
		aspect-ratio: 1;
		margin: 2px;
		animation: typing 3s ease-in-out infinite;
	}

	.dot:nth-child(2) {
		animation-delay: 0.25s;
	}

	.dot:nth-child(3) {
		animation-delay: 0.5s;
	}

	@keyframes typing {
		0% {
			transform: translateY(0);
		}
		20% {
			transform: translateY(-65%);
		}
		40% {
			transform: translateY(0);
		}
	}
</style>
