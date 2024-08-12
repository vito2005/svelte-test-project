<script lang="ts">
	import BracketL from '@src/lib/images/bracket-l.svg?component';
	import BracketR from '@src/lib/images/bracket-r.svg?component';

	export let title: string;
	export let orderNumber: string;
	export let isCurrent: boolean;
</script>

<li class="menu-item {isCurrent && 'current'}" on:click>
	<span class="item-number">{orderNumber}</span>

	<h2 class="item-title">
		<span class="bracket-l {isCurrent && 'show'}">&#123;</span>{title}<span
			class="bracket-r {isCurrent && 'show'}">&#125;</span
		>
	</h2>
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

		.bracket-l,
		.bracket-r {
			display: none;
			&.show {
				text-transform: uppercase;
				font-family: Space Grotesk;
				font-size: 30px;
				font-weight: 400;
				line-height: 36.35px;
				vertical-align: text-top;
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
	}

	@media screen and (max-width: $tablet) {
		.menu-item {
			height: 120px;
			.item-number {
				margin-bottom: 9px;
			}
			.item-title {
				margin-bottom: 9px;
				max-width: 180px;
				font-family: Space Grotesk;
				font-size: 22px;
				font-weight: 400;
				line-height: 22px;
				text-align: left;
			}
			.bracket-l,
			.bracket-r {
				&.show {
					vertical-align: text-top;
					font-family: Space Grotesk;
					font-size: 23px;
					font-weight: 400;
					text-align: left;
					line-height: 22px;
				}
			}
		}
	}

	@media screen and (max-height: $mobile-height-sm) {
		.menu-item {
			height: 100px;
		}
	}
</style>
