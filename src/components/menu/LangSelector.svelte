<script lang="ts">
	const languages = ['En', 'fr', 'sp'];
</script>

<div class="language-selector">
	<span>Lang</span>
	{#each languages as lang, index}
		<button class="lang-button" class:active={index === 0}>
			{lang}
		</button>
	{/each}
</div>

<style>
	.language-selector {
		display: flex;
		width: 304px;
		max-width: 100%;
		gap: 20px;
		justify-content: space-between;
		margin-left: 133px;
		color: rgba(16, 88, 213, 0.5);
		font-family: Space Grotesk;
		font-size: 14px;
		font-weight: 400;
		line-height: 20.3px;
		text-align: left;
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
		color: #1058d5;
	}

	@media (max-width: 991px) {
		.language-selector {
			margin-left: 10px;
		}
	}
</style>
