<script lang="ts">
	import InstagramIcon from '../../assets/icons/instagram.svg';
	import MailIcon from '../../assets/icons/mail.svg';
	import GithubIcon from '../../assets/logos/github.png';
</script>

<div class="container">
	<div class="instagram">
		<img src={InstagramIcon} alt="" />
		<a href="https://www.instagram.com/smiles_dev/" target="_blank">@smiles_dev</a>
	</div>
	<div class="github">
		<img src={GithubIcon} alt="" />
		<a href="https://github.com/jason1610" target="_blank">@jason1610</a>
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
		margin-top: 150px;
		font-size: 15px;
		gap: 10px;
		font-weight: 400;
		color: var(--text-color-tertiary);
	}

	.container > div {
		display: flex;
		align-items: center;
		gap: 5px;
	}

	.container > div > img {
		width: 20px;
		aspect-ratio: 1;
	}

	.github img {
		filter: invert(55%) sepia(33%) saturate(1526%) hue-rotate(194deg) brightness(94%) contrast(95%);
	}

	.copyright {
		color: var(--text-color-tertiary);
		font-size: 10px;
	}
</style>
