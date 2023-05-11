<script lang="ts">
	import InstagramIcon from '../assets/icons/instagram.svg';
	import MailIcon from '../assets/icons/mail.svg';
</script>

<div class="container">
	<div class="instagram">
		<img src={InstagramIcon} alt="" />
		<a href="https://www.instagram.com/smiles_dev/" target="_blank">@smiles_dev</a>
	</div>
	<div class="mail">
		<img src={MailIcon} alt="" />
		<a href="mailto:jasondanielsmiles@gmail.com">jasondanielsmiles@gmail.com</a>
	</div>
	<br />
	<p class="copyright">© 2023 by Jason Smiles</p>
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: flex-end;
		height: 300px;
		padding: 20px;
		box-sizing: border-box;
		font-size: 15px;
		gap: 10px;
		font-weight: 400;
		color: var(--text-color-tertiary);
	}

	.mail {
		display: flex;
		align-items: center;
		gap: 5px;
	}

	.mail img {
		width: 20px;
		aspect-ratio: 1;
	}

	.instagram {
		display: flex;
		align-items: center;
		gap: 5px;
	}

	.instagram img {
		width: 20px;
		aspect-ratio: 1;
	}

	.copyright {
		color: var(--text-color-tertiary);
		font-size: 10px;
	}
</style>
