<script lang="ts">
	export let title: string;
	export let orderNumber: string;
	export let isCurrent: boolean;
</script>

<li class="menu-item {isCurrent && 'current'}" on:click>
	<span class="item-number">{orderNumber}</span>
	<span class="bracket-l {isCurrent && 'show'}"><img src="/src/lib/images/bracket-l.svg" /></span>
	<h2 class="item-title">{title}</h2>
	<span class="bracket-r {isCurrent && 'show'}"><img src="/src/lib/images/bracket-r.svg" /></span>
</li>

<style lang="scss">
	.menu-item {
		display: flex;
		align-items: end;
		height: 150px;
		border-bottom: 1px solid #d9e2f3;
		&.current {
			border-left: 6px solid #1058d5;
		}
	}

	.bracket-l,
	.bracket-r {
		display: none;
		&.show {
			display: inline-block;
		}
	}

	.item-title {
		color: #1058d5;
		text-transform: uppercase;
		font:
			400 30px/1 Space Grotesk,
			sans-serif;
		margin: 0 10px;
	}

	.item-number {
		color: #1058d5;
		font-family: Space Grotesk;
		font-size: 14px;
		font-weight: 400;
		line-height: 20.3px;
		text-align: left;

		margin: 0 10px;
	}

	.item-separator {
		aspect-ratio: 1000;
		object-fit: contain;
		object-position: center;
		width: 100%;
		margin-top: 12px;
	}

	@media (max-width: 991px) {
		.item-separator {
			max-width: 100%;
		}
	}
</style>
