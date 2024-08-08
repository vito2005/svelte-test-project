<script lang="ts">
	import ArrowRight from '@src/lib/images/arrow-right.svg?component';
</script>

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

<style lang="scss">
	@use 'src/styles/index.scss' as *;

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
			color: $cyber-white;
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
</style>
