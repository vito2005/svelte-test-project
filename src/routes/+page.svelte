<script lang="ts">
	import Logo from '@src/components/Logo.svelte';
	import MobileMenu from '@src/components/menu/MobileMenu.svelte';
	import MenuIcon from '@src/components/menu/MenuIcon.svelte';
	import ArrowRight from '@src/lib/images/arrow-right.svg?component';
	import CollapseIcon from '@src/lib/images/collapse.svg?component';
	import CloseIcon from '@src/lib/images/close.svg?component';
	import ExpandIcon from '@src/lib/images/expand.svg?component';
	import vImage from '$lib/images/v-issues.jpg';
	import bgImage from '$lib/images/background-image.jpg';
	import DesktopMenu from '@src/components/menu/DesktopMenu.svelte';
	import LangSelector from '@src/components/menu/LangSelector.svelte';

	let menuOpen = false;

	const menuItems = [
		'IT Security',
		'Network maintanance',
		'Software development',
		'Contact us',
		'Projects'
	];

	const menuItemsDesctop = ['IT Security', 'Networks', 'Software', 'Projects', 'Contact us'];

	const services = [
		{
			title: 'Cyber Security',
			content: 'We handle all cyber security threats to help your business continuity'
		},
		{
			title: 'Network maintanance',
			content: 'We supply hardware and help to set up and manage a secured IT infrastructure'
		},
		{
			title: 'Software development',
			content: 'Web an app development to support cyber security for your business'
		}
	];

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

<div class="container">
	<header class="header">
		<Logo />
		<MenuIcon {menuOpen} on:click={toggleMenu} />
		<DesktopMenu menuItems={menuItemsDesctop} />
		{#if menuOpen}
			<MobileMenu {menuItems} />
		{/if}
		<LangSelector />
	</header>
	<section class="section-1">
		<div class="scroll-down">
			<div class="mouse-icon"></div>
			<p>Scroll down</p>
		</div>
		<h1 class="title">CYBER SECURITY AND IT NETWORKS MAINTANANCE</h1>
	</section>
	<section class="section-2">
		<div class="arrow-right">
			<ArrowRight />
		</div>
		<p class="subtitle">
			We protect your business continuity by searching and eliminating all kinds of cyber security
			vulnerability issues
		</p>
		<a class="audit-link" href="#">Request a security audit</a>
	</section>

	<section class="section section-3">
		<div class="header">
			<h2 class="title">SERVICES</h2>
			<div class="action-buttons">
				<CollapseIcon />
				<ExpandIcon />
				<CloseIcon />
			</div>
		</div>

		<div class="services">
			{#each services as service}
				<div class="service">
					<h3 class="service-title">{service.title}</h3>
					<p class="service-content">{service.content}</p>
				</div>
			{/each}
		</div>
	</section>

	<section class="section-4">
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
	<img class="background-image" src={bgImage} alt="Background" />
</div>

<style lang="scss">
	@use 'src/styles/index.scss' as *;
	.header {
		display: flex;
		padding: 7px;
		width: 100%;
		position: relative;
	}
	@media screen and (max-width: $desktop) {
		.header {
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 7px;
			width: 100%;
		}
	}

	.section-1 {
		display: flex;
		align-items: end;
		height: 198px;
		border-top: 2px solid #3876e333;
		border-bottom: 2px solid #3876e333;
		position: relative;
		&::before {
			content: '';
			position: absolute;
			width: 100%;
			height: 2px; /* Adjust thickness as needed */
			background-color: #3876e333; /* Color of the line */
			top: 50%;
			transform: translateY(-50%);
		}

		.title {
			width: 370px;
			margin: 0 auto;
			height: 126px;
			padding-bottom: 14px;
			color: $white;
			text-transform: uppercase;
			font-family: Space Grotesk;
			font-size: 40px;
			font-weight: 400;
			line-height: 41.8px;
		}

		.scroll-down {
			display: flex;
			align-items: center;
			color: $cyber-white;
			margin-bottom: 20px;
			p {
				margin: 0;
				margin-left: 1rem;
				width: 2rem;
				font-size: 0.8rem;
				font-family: Space Grotesk;
				font-weight: 400;
				line-height: 13.65px;
				text-align: left;
			}

			.mouse-icon {
				width: 15px;
				height: 25px;
				border: 1px solid white;
				border-radius: 12px;
				position: relative;
				margin-left: 10px;
				z-index: 1;
			}

			.mouse-icon::before {
				content: '';
				position: absolute;
				top: 8px;
				left: 50%;
				transform: translateX(-50%);
				width: 4px;
				height: 4px;
				background: white;
				border-radius: 50%;
				animation: scroll 1.5s infinite;
			}
		}
	}

	.section-2 {
		height: 200px;
		position: relative;
		background-color: rgba(255, 255, 255, 0.28);
		padding-top: 10px;

		.arrow-right {
			position: absolute;
			bottom: 32px;
			margin-left: 20px;
		}

		.subtitle {
			margin-left: 230px;
			width: 450px;
			//styleName: Mobile/Text — Big;
			font-family: Space Grotesk;
			font-size: 18px;
			font-weight: 400;
			line-height: 27.9px;
			text-align: left;
			color: $white;
		}

		.audit-link {
			position: absolute;
			bottom: 30px;
			margin-left: 230px;
			width: 200px;
			color: white;
			text-decoration: underline;
			margin-top: 20px;
			font-family: Space Grotesk;
			font-size: 16px;
			font-weight: 400;
			line-height: 23.2px;
			text-align: left;
			color: #f8faff;
		}
	}

	.section-3 {
		height: 308px;
		position: relative;
		background-color: #f8faff;
		padding-top: 10px;
		.header {
			display: flex;
			justify-content: space-between;
			.title {
				font-family: Space Grotesk;
				font-size: 16px;
				font-weight: 500;
				line-height: 23.2px;
				text-align: left;
				color: $cyber-blue;
			}

			.action-buttons {
				width: 70px;
				color: #274dbe;
			}
		}
		.services {
			display: flex;
			justify-content: flex-end;
			margin-left: 200px;

			.service {
				margin-right: 45px;
				font-family: Space Grotesk;
				color: $cyber-blue;
				text-align: left;
				&:last-child {
					margin-right: 0;
				}

				display: flex;
				flex-direction: column;

				.service-title {
					width: 50px;
					font-size: 16px;
					font-weight: 500;
					line-height: 23.2px;
					flex: 1;
				}
				.service-content {
					width: 160px;
					font-size: 14px;
					font-weight: 400;
					line-height: 20.3px;
					flex: 1;
				}
			}
		}
	}

	.section-4 {
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

	@keyframes scroll {
		0% {
			opacity: 1;
			top: 8px;
		}
		100% {
			opacity: 0;
			top: 24px;
		}
	}

	.background-image {
		position: absolute;
		top: 0;
		left: 0;
		z-index: -1;
		position: absolute;
		inset: 0;
		height: 100%;
		width: 100%;
		object-fit: cover;
		object-position: center;
	}
</style>
