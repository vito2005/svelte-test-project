<script lang="ts">
	const languages = ['En', 'Fr', 'Sp'];
</script>

<div class="language-selector">
	<span class="lang-label">Lang</span>
	{#each languages as lang, index}
		<button class="lang-button" class:active={index === 0}>
			{lang}
		</button>
	{/each}
</div>

<style lang="scss">
	@use 'src/styles/index.scss' as *;
	.language-selector {
		display: flex;
		font-family: Space Grotesk;
		font-size: 14px;
		font-weight: 400;
		line-height: 20.3px;
		text-align: left;
		.lang-button {
			cursor: pointer;
		}
	}
	@media screen and (min-width: $desktop) {
		.language-selector {
			position: absolute;
			bottom: 0px;
			right: 25px;
			color: $cyber-white;
			.lang-label {
				display: none;
			}
			.lang-button {
				color: $cyber-white;
				background: transparent;
				border: none;
				padding: none;
				margin-right: 5px;
				opacity: 0.5;
				&.active {
					opacity: 1;
				}

				&:last-child {
					margin-right: 0;
				}
			}
		}
	}

	@media screen and (max-width: $desktop) {
		.language-selector {
			width: 304px;
			max-width: 100%;
			gap: 20px;
			justify-content: space-between;
			margin-left: 133px;
			color: rgba(16, 88, 213, 0.5);
		}

		.lang-button {
			color: rgba(16, 88, 213, 0.5);
			text-transform: uppercase;
			background: none;
			border: none;
			cursor: pointer;
			padding: 0;
		}

		.lang-button.active {
			color: $cyber-blue;
		}
	}
</style>
