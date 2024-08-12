<script lang="ts">
	import BracketL from '@src/lib/images/bracket-l.svg?component';
	import BracketR from '@src/lib/images/bracket-r.svg?component';
	import { fly } from 'svelte/transition';

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
		justify-content: space-between;
	}

	.menu-item {
		position: relative;
		display: flex;
		height: 31px;
		margin-top: 5px;
		align-items: center;
		cursor: pointer;
		white-space: nowrap;

		font-family: Space Grotesk;
		font-size: 14px;
		font-weight: 400;
		line-height: 20.3px;
		text-align: left;
		color: $cyber-white;

		transition: transform 0.2s ease-in-out;

		&:last-child {
			display: flex;
			justify-content: end;
			margin-right: 0;
		}

		.bracket-l,
		.bracket-r {
			position: absolute;
			display: flex;
			align-items: center;
			transition: transform 0.5s ease-in;
			display: none;
			&.show {
				display: flex;
				color: $cyber-white;
			}
		}
		.bracket-l {
			left: -8px;

			&.show {
				transform: translateX(-8px);

				animation: bracket-l-showing 0.5s ease-in-out;
			}
		}
		@keyframes bracket-l-showing {
			0% {
				transform: translateX(0px);
			}

			100% {
				transform: translateX(-8px);
			}
		}

		.bracket-r {
			right: -8px;
			&.show {
				transform: translateX(8px);

				animation: bracket-r-showing 0.5s ease-in-out;
			}
		}

		@keyframes bracket-r-showing {
			0% {
				transform: translateX(0px);
			}

			100% {
				transform: translateX(8px);
			}
		}

		&:hover {
			transform: scale(1.1);
		}
	}

	@media screen and (max-width: $desktop) {
		.menu-navigation {
			display: none;
		}
	}
</style>
