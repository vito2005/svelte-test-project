<script lang="ts">
	import BracketL from '@src/lib/images/bracket-l.svg?component';
	import BracketR from '@src/lib/images/bracket-r.svg?component';

	export let menuItems: string[];
	export let selectedItem: string = menuItems[0];

	const bracketSize = 0.5;

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
				><BracketL transform="scale({bracketSize})" /></span
			>

			<span class="item-title">{item}</span>
			<span class="bracket-r {item === selectedItem && 'show'}"
				><BracketR transform="scale({bracketSize})" /></span
			>
		</div>
	{/each}
</div>

<style lang="scss">
	@use 'src/styles/index.scss' as *;

	.menu-navigation {
		display: flex;
		width: 100%;
		margin-left: 130px;
		margin-right: 22px;
	}

	.menu-item {
		height: 31px;
		display: flex;
		align-items: center;
		cursor: pointer;
		margin-right: 180px;
		white-space: nowrap;

		font-family: Space Grotesk;
		font-size: 14px;
		font-weight: 400;
		line-height: 20.3px;
		text-align: left;
		color: $cyber-white;
		&:last-child {
			display: flex;
			justify-content: end;
			margin-right: 0;
			width: 100%;
		}
		.bracket-l,
		.bracket-r {
			display: none;
			&.show {
				display: flex;
				color: $cyber-white;
			}
		}
		.bracket-l {
			margin-right: 7px;
		}
		.bracket-r {
			margin-left: 7px;
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
