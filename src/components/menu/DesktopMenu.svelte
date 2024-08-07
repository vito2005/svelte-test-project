<script lang="ts">
	import BracketL from '@src/lib/images/bracket-l.svg?component';
	import BracketR from '@src/lib/images/bracket-r.svg?component';

	export let menuItems: string[];
	export let selectedItem: string = menuItems[0];

	function handleMenuItemClick(item: string) {
		selectedItem = item;
	}
</script>

<div class="menu-navigation">
	{#each menuItems as item, index}
		<div
			class="menu-item {item === selectedItem && 'current'}"
			on:click={() => handleMenuItemClick(item)}
		>
			<span class="bracket-l {item === selectedItem && 'show'}"
				><BracketL transform="scale(0.7)" /></span
			>
			<span class="item-title">{item}</span>
			<span class="bracket-r {item === selectedItem && 'show'}"
				><BracketR transform="scale(0.7)" /></span
			>
		</div>
	{/each}
</div>

<style lang="scss">
	@use 'src/styles/index.scss' as *;

	.menu-navigation {
		display: flex;
		justify-content: space-between;
		width: 100%;
		margin-left: 130px;
	}

	.menu-item {
		display: flex;
		align-items: start;
		cursor: pointer;
		margin-right: 180px;

		font-family: Space Grotesk;
		font-size: 14px;
		font-weight: 400;
		line-height: 20.3px;
		text-align: left;
		color: $cyber-white;
		.bracket-l,
		.bracket-r {
			display: none;
			&.show {
				display: inline-block;
				color: $cyber-white;
			}
		}
		&:last-child {
			margin-right: 0;
		}
	}

	.bracket-r.show path {
		transform: scale(0.5) !important; /* Add !important to override other styles */
	}

	@media screen and (max-width: $desktop) {
		.menu-navigation {
			display: none;
		}
	}
</style>
