<script lang="ts">
	import BracketL from '@src/lib/images/bracket-l.svg?component';
	import BracketR from '@src/lib/images/bracket-r.svg?component';

	export let title: string;
	export let orderNumber: string;
	export let isCurrent: boolean;
</script>

<li class="menu-item {isCurrent && 'current'}" on:click>
	<span class="item-number">{orderNumber}</span>
	<span class="bracket-l {isCurrent && 'show'}"><BracketL /></span>
	<h2 class="item-title">{title}</h2>
	<span class="bracket-r {isCurrent && 'show'}"><BracketR /></span>
</li>

<style lang="scss">
	@use 'src/styles/index.scss' as *;

	.menu-item {
		display: flex;
		align-items: end;
		height: 150px;
		border-bottom: 1px solid #d9e2f3;
		cursor: pointer;
		&.current {
			border-left: 6px solid $cyber-blue;
			.item-number {
				margin-left: 16px;
				margin-right: 82px;
			}
		}
	}

	.bracket-l,
	.bracket-r {
		display: none;
		&.show {
			display: inline-block;
			color: $cyber-blue;
			margin-left: -8px;
			margin-right: 8px;
		}
	}

	.bracket-l {
		&.show {
			margin-left: -8px;
			margin-right: 8px;
		}
	}

	.bracket-r {
		&.show {
			margin-left: 8px;
			margin-right: -8px;
		}
	}

	.item-title {
		color: $cyber-blue;
		text-transform: uppercase;
		font-family: Space Grotesk;
		font-size: 30px;
		font-weight: 400;
		line-height: 36.35px;
		text-align: left;

		margin: 0;
	}

	.item-number {
		color: $cyber-blue;
		font-family: Space Grotesk;
		font-size: 14px;
		font-weight: 400;
		line-height: 20.3px;
		text-align: left;

		margin: 0 94px 0 22px;
	}

	.item-separator {
		aspect-ratio: 1000;
		object-fit: contain;
		object-position: center;
		width: 100%;
		margin-top: 12px;
	}

	@media (max-width: $desktop) {
		.item-separator {
			max-width: 100%;
		}
	}
</style>
