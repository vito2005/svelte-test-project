<script lang="ts">
	import { fly } from 'svelte/transition';
	import LangSelector from './LangSelector.svelte';
	import MenuItem from './MobileMenuItem.svelte';

	export let menuItems: string[];
	export let selectedItem: string = menuItems[0];

	function handleMenuItemClick(item: string) {
		selectedItem = item;
	}
</script>

<main class="services-menu" transition:fly={{ x: 200, duration: 500 }}>
	<ul class="menu-navigation">
		{#each menuItems as item, index}
			<MenuItem
				title={item}
				orderNumber={`0${index + 1}`}
				on:click={() => handleMenuItemClick(item)}
				isCurrent={item === selectedItem}
			/>
		{/each}
	</ul>

	<footer class="menu-footer">
		<LangSelector />
	</footer>
</main>

<style lang="scss">
	@use 'src/styles/index.scss' as *;
	@media screen and (min-width: $desktop) {
		.services-menu {
			display: none;
		}
	}
	@media screen and (max-width: $desktop) {
		.services-menu {
			position: fixed;
			top: 0;
			left: 0;
			z-index: 2;
			height: 100vh;
			background-color: $cyber-white;
			display: flex;
			width: 100%;
			flex-direction: column;
			.menu-footer {
				position: absolute;
				bottom: 50px;
				left: 22px;
			}
		}

		.menu-header {
			align-self: flex-end;
			position: relative;
			aspect-ratio: 1;
			margin-right: 22px;
			width: 18px;
		}

		.logo-background {
			position: absolute;
			inset: 0;
			height: 100%;
			width: 100%;
			object-fit: cover;
			object-position: center;
		}

		.logo {
			aspect-ratio: 1;
			object-fit: contain;
			object-position: center;
			width: 100%;
		}

		.menu-navigation {
			margin: 0;
			padding: 0;
			list-style-type: none;
		}

		.menu-item.current {
			color: $cyber-blue;
		}
	}
</style>
