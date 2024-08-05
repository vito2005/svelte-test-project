<script lang="ts">
	import Logo from '@src/components/Logo.svelte';
	import Menu from '@src/components/menu/Menu.svelte';
	import MenuIcon from '@src/components/menu/MenuIcon.svelte';
	import ArrowRight from '@src/lib/images/arrow-right.svg?component';
	import CollapseIcon from '@src/lib/images/collapse.svg?component';
	import CloseIcon from '@src/lib/images/close.svg?component';
	import ExpandIcon from '@src/lib/images/expand.svg?component';
	import vImage from '$lib/images/v-issues.jpg';
	import bgImage from '$lib/images/background-image.jpg';

	let menuOpen = false;

	const menuItems = [
		'IT Security',
		'Network maintanance',
		'Software development',
		'Contact us',
		'Projects'
	];

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
		{#if menuOpen}
			<Menu {menuItems} />
		{/if}
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
		<h2 class="title">SERVICES</h2>
		<div class="action-buttons">
			<CollapseIcon />
			<ExpandIcon />
			<CloseIcon />
		</div>
		<div class="services">
			{#each services as service}
				<div class="service">
					<h3>{service.title}</h3>
					<p>{service.content}</p>
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
			<div class="issues">
				{#each issues as issue}
					<div class="issue">
						<h3>{issue.title}</h3>
						<p>{issue.issue1}</p>
						<p>{issue.issue2}</p>
					</div>
				{/each}
			</div>
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
	.header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 7px;
		width: 100%;
	}
	.container {
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
			color: #fff;
			text-transform: uppercase;
			font-family: Space Grotesk;
			font-size: 40px;
			font-weight: 400;
			line-height: 41.8px;
		}

		.scroll-down {
			display: flex;
			align-items: center;
			color: #e6edfa;
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
			color: #fff;
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
		.action-buttons {
			color: red;
		}
	}

	.section-4 {
		.action-buttons {
			color: red;
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
