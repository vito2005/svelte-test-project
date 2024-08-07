<script>
	export let menuOpen = false;
</script>

<div class="menu-icon" class:open={menuOpen} on:click>
	<div class="bar1"></div>
	<div class="bar2"></div>
	<div class="bar3"></div>
</div>

<style lang="scss">
	@use 'src/styles/index.scss' as *;

	@media screen and (min-width: $desktop) {
		.menu-icon {
			display: none;
		}
	}

	@media screen and (max-width: $desktop) {
		.menu-icon {
			position: absolute;
			top: 36px;
			right: 22px;
			display: flex;
			flex-direction: column;
			justify-content: space-around;
			width: 24px;
			height: 24px;
			cursor: pointer;
			z-index: 100;
		}

		.menu-icon div {
			width: 24px;
			height: 2px;
			background-color: rgba(230, 237, 250, 1);
			transition: all 0.3s ease-in-out;
		}

		.open .bar1,
		.open .bar2,
		.open .bar3 {
			background-color: rgba(16, 88, 213, 1);
		}

		.bar1 {
			transform-origin: center;
		}

		.bar2 {
			transform-origin: center;
		}

		.bar3 {
			transform-origin: center;
		}

		.open .bar1 {
			transform: rotate(45deg) translate(6px, 6px);
		}

		.open .bar2 {
			opacity: 0;
		}

		.open .bar3 {
			transform: rotate(-45deg) translate(5px, -5px);
		}
	}
</style>
