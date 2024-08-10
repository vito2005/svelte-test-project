<script lang="ts">
	import Logo from '@src/components/Logo.svelte';
	import MobileMenu from '@src/components/menu/MobileMenu.svelte';
	import MenuIcon from '@src/components/menu/MenuIcon.svelte';
	import CollapseIcon from '@src/lib/images/collapse.svg?component';
	import CloseIcon from '@src/lib/images/close.svg?component';
	import ExpandIcon from '@src/lib/images/expand.svg?component';
	import vImage from '$lib/images/v-issues.jpg';
	import DesktopMenu from '@src/components/menu/DesktopMenu.svelte';
	import LangSelector from '@src/components/menu/LangSelector.svelte';
	import Section1 from './sections/Section1.svelte';

	let menuOpen = false;
	let innerWidth: number;

	const menuItems = [
		'IT Security',
		'Network maintanance',
		'Software development',
		'Contact us',
		'Projects'
	];

	const menuItemsDesctop = ['IT Security', 'Networks', 'Software', 'Projects', 'Contact us'];

	const issues = [
		{
			title: 'Web security vulnerabilities',
			issue1: 'Database securiity',
			issue2: 'Cloud servers security'
		},
		{
			title: 'Network vulnerabilities',
			issue1: 'USB robbing',
			issue2: 'Printer hacking'
		},
		{
			title: 'Social engeneering attacks',
			issue1: 'Email security',
			issue2: 'Phishing protection'
		}
	];

	function toggleMenu() {
		menuOpen = !menuOpen;

		if (menuOpen) {
			document.body.style.overflow = 'hidden';
		} else {
			document.body.style.overflow = 'auto';
		}
	}
</script>

<svelte:window bind:innerWidth />

<div class="container">
	<header class="header">
		<Logo />
		<MenuIcon {menuOpen} on:click={toggleMenu} />
		<DesktopMenu menuItems={menuItemsDesctop} />
		{#if menuOpen}
			<MobileMenu {menuItems} />
		{/if}
		<div class="lang-selector-wrapper">
			<LangSelector />
		</div>
	</header>

	<Section1 />

	<section class="section-3">
		<div class="title">
			We solve any kind of cyber security vulnerability issues to keep your business secured
		</div>
		<div class="vulterability-image">
			<img src={vImage} alt="vulterability image" />
		</div>
		<div class="vulterability-issues">
			{#each issues as issue}
				<div class="issue">
					<h3>{issue.title}</h3>
					<p>{issue.issue1}</p>
					<p>{issue.issue2}</p>
				</div>
			{/each}
		</div>
		<div class="report-issue">
			<div class="title">Can’t fix a vulnerability issue? We can help!</div>
			<div class="action-buttons">
				<CollapseIcon />
				<ExpandIcon />
				<CloseIcon />
			</div>
			<a href="#">Report an issue</a>
		</div>
	</section>
</div>

<style lang="scss">
	@use 'src/styles/index.scss' as *;

	.container {
		overflow: hidden;
		max-width: $desktop-max;
		margin: 0 auto;
		background:
			linear-gradient(180deg, rgba(12, 101, 255, 0.79) 0%, rgba(12, 101, 255, 0.79) 100%) 0% 0%
				no-repeat padding-box,
			url('$lib/images/background-image.jpg') 49% -86%/110% auto;
	}
	@media screen and (max-width: $desktop) {
		.container {
			background:
				linear-gradient(180deg, rgba(12, 101, 255, 0.79) 0%, rgba(12, 101, 255, 0.79) 100%) 0% 0%
					no-repeat padding-box,
				url('$lib/images/background-image.jpg') 98% -24%/145% auto;
		}
	}

	.header {
		display: flex;
		padding: 0;
		padding-left: 10px;
		width: 100%;
		position: relative;
		height: 100px;
	}

	.section-3 {
		background: $cyber-white;

		display: grid;
		grid-template-rows: repeat(2, 350px);
		grid-template-columns: repeat(2, 1fr);

		.title {
			width: 764px;
			height: 188px;
			margin-left: 30px;
			margin-top: 41px;
			font-family: Space Grotesk;
			font-size: 45px;
			font-weight: 400;
			line-height: 47.03px;
			text-align: left;
			letter-spacing: 2px;
			color: $cyber-blue;
			text-transform: uppercase;

			grid-column-start: 1;
			grid-column-end: 4;
		}
		.vulterability-image {
			position: relative;
			img {
				position: absolute;
				right: 0;
				width: 454px;
				height: 300px;
			}
		}
		.vulterability-issues {
			grid-column: 2/5;
			grid-row-start: 2;
			display: flex;
			align-items: end;
			justify-content: space-between;
			.issue {
				color: $cyber-blue;
				margin-right: 50px;
				margin-bottom: 10px;

				h3 {
					width: 150px;
					font-family: Space Grotesk;
					font-size: 16px;
					font-weight: 500;
					line-height: 23.2px;
					text-align: left;
				}
				p {
					font-family: Space Grotesk;
					font-size: 14px;
					font-weight: 400;
					line-height: 20.3px;
					text-align: left;
				}
			}
		}

		.report-issue {
			grid-column-start: 1;
			grid-column-end: 2;
			height: 200px;
			width: 450px;
			align-self: end;
			padding: 0 30px;
			position: relative;
			background: $cyber-blue;
			.title {
				width: 280px;
				margin: 0;
				margin-top: 30px;
				font-family: Space Grotesk;
				font-size: 18px;
				font-weight: 400;
				line-height: 27.9px;
				text-align: left;
				text-transform: none;
				color: $white;
			}

			.action-buttons {
				position: absolute;
				top: 20px;
				right: 20px;
				color: $cyber-white;
				display: flex;
				align-items: end;
				height: 28px;
				justify-content: space-between;
				width: 58px;
			}
			a {
				position: absolute;
				bottom: 20px;
				font-family: Space Grotesk;
				font-size: 16px;
				font-weight: 400;
				line-height: 23.2px;
				text-align: left;
				color: $cyber-white;
			}
		}
	}
	@media screen and (max-width: $desktop) {
		.header {
			display: flex;
			justify-content: space-between;
			align-items: center;
			width: 100%;

			.lang-selector-wrapper {
				display: none;
			}
		}

		.section-3 {
			height: 642px;
			grid-template-rows: repeat(3, 1fr);
			grid-template-columns: repeat(4, 1fr);

			.title {
				width: 480px;
				margin: 20px 15px;
				font-size: 30px;
				font-weight: 400;
				line-height: 31.35px;
				text-align: left;
				color: $cyber-blue;
				letter-spacing: normal;
			}

			.vulterability-image {
				position: relative;
				img {
					position: absolute;
					right: 0;
					width: auto;
					height: auto;
				}
			}

			.vulterability-issues {
				margin-top: 30px;
				grid-column-start: 2;
				grid-column-end: 5;
				display: flex;
				align-items: start;
				.issue {
					color: $cyber-blue;
					margin-right: 50px;
					&:last-child {
						margin-right: 0;
					}

					h3 {
						font-family: Space Grotesk;
						font-size: 16px;
						font-weight: 500;
						line-height: 23.2px;
						text-align: left;
					}
					p {
						font-family: Space Grotesk;
						font-size: 14px;
						font-weight: 400;
						line-height: 20.3px;
						text-align: left;
					}
				}
			}

			.report-issue {
				height: 200px;
				width: auto;
				grid-column-start: 2;
				grid-column-end: 5;

				position: relative;
				background: $cyber-blue;
				.title {
					width: 280px;
					margin: 0;
					margin-top: 21px;

					font-family: Space Grotesk;
					font-size: 18px;
					font-weight: 400;
					line-height: 27.9px;
					text-align: left;
					text-transform: none;
					color: $white;
				}

				.action-buttons {
					position: absolute;
					top: 10px;
					right: 20px;
					color: $cyber-white;
					display: flex;
					align-items: end;
					height: 28px;
					justify-content: space-between;
					width: 58px;
				}
				a {
					position: absolute;
					bottom: 25px;
					font-family: Space Grotesk;
					font-size: 16px;
					font-weight: 400;
					line-height: 23.2px;
					text-align: left;
					color: $cyber-white;
				}
			}
		}
	}

	@media screen and (max-width: $tablet) {
		.container {
			background:
				linear-gradient(180deg, rgba(12, 101, 255, 0.79) 0%, rgba(12, 101, 255, 0.79) 100%) 0% 0%
					no-repeat padding-box,
				url('/src/lib/images/background-image.jpg') 47% -74%/331% auto;
		}
		.section-3 {
			height: auto;
			display: flex;
			flex-direction: column;
			.title {
				order: 2;
				max-width: 330px;
				font-size: 30px;
				font-weight: 400;
				line-height: 31.35px;
				text-align: left;
			}
			.vulterability-issues {
				order: 3;
				flex-direction: column;

				.issue {
					display: grid;
					grid-template-columns: repeat(2, 1fr);
					grid-template-rows: repeat(2, 1fr);
					margin-right: 0;
					margin-left: 20px;
					margin-top: 50px;
					gap: 0px 40px;
					&:last-child {
						margin-left: 20px;
					}

					h3 {
						grid-row: 1/3;
						margin: 0;
					}

					p {
						margin: 0;
					}
				}
			}
			.vulterability-image {
				order: 1;
				img {
					position: static;
					width: 100%;
				}
			}

			.report-issue {
				order: 4;
				margin-top: 0px;
				padding: 0;
				width: 100%;
				position: relative;
				height: 200px;

				.action-buttons {
					position: absolute;
					top: 10px;
				}

				.title {
					width: 100%;
					margin-left: 20px;
					align-items: center;
					display: flex;
				}
				a {
					margin-left: 20px;
					bottom: 24px;
				}
			}
		}
	}
</style>
