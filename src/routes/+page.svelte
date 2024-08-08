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
	}

	.section-3 {
		height: 642px;
		background: $cyber-white;

		display: grid;
		grid-template-rows: repeat(3, 1fr);
		grid-template-columns: repeat(4, 1fr);
		.title {
			width: 480px;
			margin: 20px 15px;
			text-transform: uppercase;
			font-family: Space Grotesk;
			font-size: 30px;
			font-weight: 400;
			line-height: 31.35px;
			text-align: left;
			color: $cyber-blue;

			grid-column-start: 1;
			grid-column-end: 4;
		}
		.vulterability-image {
			position: relative;
			img {
				position: absolute;
				right: 0;
			}
		}
		.vulterability-issues {
			margin-top: 45px;
			grid-column-start: 2;
			grid-column-end: 5;
			display: flex;
			.issue {
				color: $cyber-blue;
				margin-right: 50px;
				&:last-child {
					margin-right: 0;
					margin-left: 40px;
				}

				h3 {
					width: 110px;
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
			grid-column-start: 2;
			grid-column-end: 5;

			position: relative;
			background: $cyber-blue;
			padding: 21px;
			margin-top: 20px;
			.title {
				width: 280px;
				margin: 0;

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

	.background-image {
		position: absolute;
		top: 0;
		left: 0;
		max-width: $desktop-max;
		margin: 0 auto;
		z-index: -1;
		inset: 0;
		height: 100%;
		width: 100%;
		object-fit: cover;
		object-position: center;
	}
	@media (max-width: $desktop) {
		.background-image {
			height: auto;
			object-fit: cover;
			object-position: 0px 0px;
		}
	}
</style>
