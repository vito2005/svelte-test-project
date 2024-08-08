<script>
	import logo from '$lib/images/logo.svg?url';
</script>

<div class="logo">
	<img src={logo} alt="Logo" />
	<span class="logo-text">Secure</span>
	<span class="logo-text">authorities</span>
</div>

<style lang="scss">
	@use 'src/styles/index.scss' as *;

	@media screen and (min-width: $desktop) {
		.logo {
			margin-top: 5px;
		}
	}
	.logo {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: flex-start;
	}

	.logo img {
		width: 24px;
		height: 29px;
		margin-right: 10px;
		margin-bottom: 13px;
	}

	.logo-text {
		font-family: 'Space Grotesk', sans-serif;
		font-optical-sizing: auto;
		font-size: 14px;
		font-weight: 400;
		line-height: 17.5px;
		text-align: left;
		color: rgba(230, 237, 250, 1);
	}
</style>
