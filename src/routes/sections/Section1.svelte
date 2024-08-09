<script lang="ts">
	import ArrowRight from '@src/lib/images/arrow-right.svg?component';
	import CollapseIcon from '@src/lib/images/collapse.svg?component';
	import CloseIcon from '@src/lib/images/close.svg?component';
	import ExpandIcon from '@src/lib/images/expand.svg?component';

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
</script>

<section class="section-1">
	<div class="scroll-down">
		<div class="mouse-icon"></div>
		<p>Scroll down</p>
	</div>
	<div class="empty-space"></div>
	<div class="title">
		<h1 class="title-text">CYBER SECURITY AND IT NETWORKS MAINTANANCE</h1>
	</div>

	<div class="subtitle">
		<p class="subtitle-text">
			We protect your business continuity by searching and eliminating all kinds of cyber security
			vulnerability issues
		</p>
		<div class="arrow-right">
			<ArrowRight />
		</div>
		<a class="audit-link" href="#">Request a security audit</a>
		<div class="empty-content"></div>
	</div>

	<div class="services-wrapper">
		<div class="services-header">
			<h2 class="services-title">SERVICES</h2>
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
	</div>
</section>

<style lang="scss">
	@use 'src/styles/index.scss' as *;
	$line-color: rgba(56, 118, 227, 1);
	.section-1 {
		height: 600px;
		position: relative;
		display: grid;
		grid-template-rows: 200px 200px;
		grid-template-columns: repeat(2, 1fr);
		background-image: linear-gradient(
			$line-color,
			$line-color 1px,
			transparent 1px,
			transparent 100px,
			$line-color 100px,
			$line-color 101px,
			transparent 101px,
			transparent 100%
		);
		.empty-space {
			grid-column: 1 / 3;
			height: 200px;
		}

		.title {
			color: $white;
			padding-left: 30px;
			padding-top: 42px;
			grid-row: 2/4;
			background: rgba(255, 255, 255, 0.1);
			.title-text {
				text-transform: uppercase;
				width: 592px;
				font-family: Space Grotesk;
				font-size: 63px;
				font-weight: 400;
				line-height: 67.93px;
				text-align: left;
				margin: 0;
				letter-spacing: 3px;
			}
		}
		.subtitle {
			position: relative;
			color: $white;
			display: grid;
			grid-template-columns: 1fr 0.65fr;
			grid-template-rows: repeat(2, 1fr);

			.subtitle-text {
				width: 100%;
				padding: 15px;
				margin: 0;
				font-family: Space Grotesk;
				font-size: 18px;
				font-weight: 400;
				line-height: 27.9px;
				text-align: left;
				grid-row: 1/3;
				grid-column: 1/2;
				background-color: rgba(255, 255, 255, 0.18);
			}
			.arrow-right {
				display: block;
				position: absolute;
				bottom: 10px;
				left: 15px;
			}

			.audit-link {
				color: #f8faff;
				position: absolute;
				align-self: end;
				margin-left: 45px;
				margin-bottom: 10px;
				font-family: Space Grotesk;
				font-size: 16px;
				font-weight: 400;
				line-height: 23.2px;
				text-align: left;
			}

			.empty-content {
				grid-row: 1/3;
				grid-column: 2 / 3;
				width: 100%;
				justify-self: end;
				background-image: linear-gradient(
					$line-color,
					$line-color 1px,
					transparent 1px,
					transparent 100px,
					$line-color 100px,
					$line-color 101px,
					transparent 101px,
					transparent 100%
				);
			}
		}

		.arrow-right {
			display: none;
		}

		.scroll-down {
			position: absolute;
			bottom: 22px;
			display: flex;
			align-items: center;
			color: $cyber-white;
			margin-left: 30px;
			p {
				margin: 0;
				margin-left: 1rem;
				width: 6rem;
				font-size: 1rem;
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
		}

		.services-wrapper {
			height: 200px;
			position: relative;
			background-color: #f8faff;
			grid-column: 2 / 3;
			.services-header {
				display: flex;
				justify-content: space-between;
				padding-top: 10px;

				.action-buttons {
					position: absolute;
					top: 5px;
					right: 16px;
					display: flex;
					align-items: end;
					height: 28px;
					justify-content: space-between;
					width: 58px;
					color: #274dbe;
				}
				.services-title {
					display: none;
				}
			}
			.services {
				display: flex;
				margin-left: 20px;
				margin-top: 55px;
				justify-content: space-between;

				.service {
					max-width: 260px;
					font-family: Space Grotesk;
					color: $cyber-blue;
					text-align: left;
					&:last-child {
						margin-right: 0;
					}

					display: flex;
					flex-direction: column;

					.service-title {
						font-size: 16px;
						font-weight: 500;
						line-height: 23.2px;
						flex: 1;
					}
					.service-content {
						margin-top: 0;
						max-width: 190px;
						font-size: 14px;
						font-weight: 400;
						line-height: 20.3px;
						flex: 1;
					}
				}
			}
		}
	}

	@media screen and (max-width: $desktop) {
		.section-1 {
			height: 700px;
			display: flex;
			flex-direction: column;
			background-image: linear-gradient(
				$line-color,
				$line-color 1px,
				transparent 1px,
				transparent 100px,
				$line-color 100px,
				$line-color 101px,
				transparent 101px,
				transparent 100%
			);
			.empty-space {
				display: none;
			}
			.title {
				display: flex;
				align-items: center;
				height: 200px;
				margin: 0;
				padding: 0;

				.title-text {
					width: 370px;
					margin-left: 200px;
					margin-top: 0;
					margin-bottom: -40px;
					text-transform: uppercase;
					font-family: Space Grotesk;
					font-size: 40px;
					font-weight: 400;
					line-height: 41.8px;
					letter-spacing: normal;
				}
			}

			.subtitle {
				display: block;
				height: 200px;
				position: relative;
				background-color: rgba(255, 255, 255, 0.28);
				font-family: Space Grotesk;
				font-size: 18px;
				font-weight: 400;
				line-height: 27.9px;
				text-align: left;

				.subtitle-text {
					position: relative;
					background-color: transparent;
					padding: 0;
					width: 450px;
					margin-left: 200px;
					margin-top: 25px;
				}

				.arrow-right {
					display: block;
					position: absolute;
					bottom: 15px;
					color: $cyber-white;
				}

				.audit-link {
					position: absolute;
					bottom: 15px;
					margin-left: 200px;
					margin-bottom: 0;
					width: 200px;
					text-decoration: underline;
					font-family: Space Grotesk;
					font-size: 16px;
					font-weight: 400;
					line-height: 23.2px;
					text-align: left;
				}
			}

			.services-wrapper {
				height: 300px;
				.services-header {
					display: flex;
					justify-content: space-between;
					padding-top: 15px;
					.services-title {
						display: block;
						margin-left: 20px;

						font-family: Space Grotesk;
						font-size: 16px;
						font-weight: 500;
						line-height: 23.2px;
						text-align: left;
						color: $cyber-blue;
					}

					.action-buttons {
						position: static;
						display: flex;
						align-items: end;
						height: 28px;
						justify-content: space-between;
						width: 58px;
						margin-right: 20px;
						color: #274dbe;
					}
				}
				.services {
					display: flex;
					margin-left: 200px;
					margin-top: 55px;

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

			.scroll-down {
				top: 37%;
				bottom: auto;
				display: flex;
				align-items: center;
				color: $cyber-white;
				margin-left: 0px;
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
			}
		}
	}

	@media screen and (max-width: $tablet) {
		.section-1 {
			height: 1300px;
			.title {
				height: 300px;
				.title-text {
					height: inherit;
					margin-left: 20px;
					margin-top: 76px;

					max-width: 265px;
					font-size: 40px;
					font-weight: 400;
					line-height: 41.8px;
					text-align: left;
				}
			}

			.subtitle {
				height: 300px;
				.subtitle-text {
					height: inherit;
					margin-left: 20px;
					max-width: 310px;
					font-size: 18px;
					font-weight: 400;
					line-height: 27.9px;
					text-align: left;
				}
				.audit-link {
					margin-left: 60px;
				}
			}
			.scroll-down {
				display: none;
			}

			.services-wrapper {
				height: 500px;
				.services {
					margin: 0;
					flex-direction: column;

					.service {
						margin: 0;
						margin-left: 20px;
						.service-title {
							width: 200px;
						}
						.service-content {
							width: 300px;
						}
					}
				}
			}
		}
	}
</style>
