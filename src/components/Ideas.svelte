<script lang="ts">
	import TSLogo from '../assets/typescript-logo.png';
	let texts: string[] = [
		'Maybe someting with ai?',
		'How about a better way to do email..',
		'Hmmmmm...'
	];
	let displayText: string = '';
	let index: number = 0;
	let isDeleting: boolean = false;

	const type = () => {
		const textIndex: number = index % texts.length;
		const currentText: string = texts[textIndex];
		const currentLength: number = displayText.length;

		if (isDeleting) {
			displayText = currentText.slice(0, currentLength - 1);
		} else {
			displayText = currentText.slice(0, currentLength + 1);
		}

		let typeSpeed: number = isDeleting ? 50 : 100;

		if (!isDeleting && currentLength === currentText.length) {
			typeSpeed = 2000;
			isDeleting = true;
		} else if (isDeleting && currentLength === 0) {
			isDeleting = false;
			index++;
			typeSpeed = 500;
			displayText = '';
		}

		setTimeout(type, typeSpeed);
	};

	type();
</script>

<div class="card">
	<div class="top">
		<div class="tab">
			<img src={TSLogo} alt="" />
			<h3>ideas.ts</h3>
		</div>
		<div class="fill" />
	</div>
	<div class="text">
		<div class="line-numbers">
			<p>1</p>
			<p>2</p>
			<p>3</p>
			<p>4</p>
			<p>5</p>
			<p>6</p>
			<p>7</p>
			<p>8</p>
			<p>9</p>
			<p>10</p>
			<p>11</p>
			<p>12</p>
			<p>13</p>
		</div>
		<p>
			&lt;<span class="pink">script</span> <span class="green">lang</span><span class="pink">=</span
			> <span class="yellow">"ts"</span>&gt;
		</p>

		<p>//I've got some projects in the works,</p>
		<p>//but im always looking for new ideas..</p>
		<br />
		<p>
			//<span>{displayText}<span class="caret">█</span></span>
		</p>
		<p>
			&lt;/<span class="pink">script</span> &gt;
		</p>
	</div>
</div>

<style>
	.card {
		width: 400px;
		max-width: 90vw;
		background-color: var(--card-background-color-primary);
		outline: 1.5px solid var(--card-stroke-color-primary);
		border-radius: 10px;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		gap: 20px;
		overflow: hidden;
		min-height: 275px;
	}

	.top {
		/* background-color: var(--card-background-color-primary); */
		height: 40px;
		display: flex;
	}

	.tab {
		display: flex;
		justify-content: center;
		gap: 7px;
		align-items: center;
		padding: 0 20px;
		height: 100%;
		border-radius: 10px 10px 0 0;
		box-shadow: 0px -20px 0px 16px var(--card-stroke-color-primary);
	}

	.tab img {
		height: 15px;
		/* filter: saturate(0); */
	}

	.tab h3 {
		font-weight: 400;
		color: var(--text-color-secondary);
		font-size: 15px;
	}

	.fill {
		background-color: red;
		background-color: var(--card-stroke-color-primary);
		width: 100%;
	}

	.text {
		padding: 30px;
		padding-top: 0;
		position: relative;
	}

	.line-numbers {
		position: absolute;
		left: 5px;
		text-align: right;
		user-select: none;
	}

	.line-numbers p {
		color: rgba(74, 138, 181, 0.607);
	}

	p {
		color: var(--text-color-secondary);
	}

	.caret {
		animation: blink 1s infinite;
	}

	@keyframes blink {
		0%,
		50% {
			opacity: 1;
		}
		51%,
		100% {
			opacity: 0;
		}
	}

	.pink {
		color: #ff79c6;
	}
	.green {
		color: #50fa7b;
	}
	.yellow {
		color: #f1fa8c;
	}
</style>
