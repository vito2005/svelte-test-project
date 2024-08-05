<script lang="ts">
	import { fly } from 'svelte/transition';
	import LangSelector from './LangSelector.svelte';
	import MenuItem from './MenuItem.svelte';

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

<style>
	.services-menu {
		position: absolute;
		top: 0;
		left: 0;
		z-index: 2;
		height: 100vh;
		background-color: #e6edfa;
		display: flex;
		width: 100%;
		max-width: 800px;
		flex-direction: column;
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

	.menu-footer {
		margin-top: auto;
	}

	.menu-item.current {
		color: #1058d5;
	}

	@media (max-width: 991px) {
	}
</style>
