<script lang="ts">
	export let animation = true;
	let innerWidth: number;

	function typewriter(node: HTMLElement, { speed = 2, delay = 1500 }) {
		const text = node.textContent!;
		const duration = text.length / (speed * 0.01);

		return {
			duration,
			tick: (t: number) => {
				const i = Math.trunc(text.length * t);
				node.textContent = text.slice(0, i);
			},
			delay
		};
	}
</script>

<svelte:window bind:innerWidth />
<div class="logo" class:animation>
	<svg width="30" height="30" viewBox="0 0 22 30" fill="none" xmlns="http://www.w3.org/2000/svg">
		<path
			fill-rule="evenodd"
			clip-rule="evenodd"
			d="M20.953 10.2997C20.3757 12.1339 19.8428 13.9869 19.2129 15.7996C18.1028 19.0076 16.6272 21.9933 14.5574 24.5781C12.7711 26.8094 10.6647 28.5066 7.97491 29.0601C6.90204 29.2845 5.77982 29.1994 4.68065 29.2599C4.18716 29.2858 3.95694 28.8807 3.69367 28.5304C2.15734 26.4853 1.25835 24.0935 0.681997 21.5407C-0.114334 18.0399 -0.0507856 14.4695 0.0767764 10.9009C0.112159 9.87389 0.368446 8.85573 0.422916 7.82876C0.441844 7.52397 0.521537 7.22768 0.656215 6.96139C0.790893 6.69511 0.977178 6.46549 1.20156 6.28922C2.62363 5.00448 4.22857 3.99277 5.95022 3.29582C6.52844 3.04988 7.11992 2.84692 7.70629 2.62273C8.76496 2.22199 9.83387 2.02214 10.9531 2.31415C11.447 2.40112 11.9458 2.4499 12.4459 2.46016C11.3034 3.05946 10.3153 3.49049 9.40696 4.07297C8.04521 4.94668 6.50888 5.27908 5.09243 5.95708C4.05537 6.46897 3.05379 7.0655 2.09589 7.74178C1.75863 7.99761 1.52406 8.38929 1.44178 8.83398C0.918965 12.8748 0.756486 16.9154 1.80724 20.9057C2.28088 22.7564 3.107 24.472 4.22953 25.9362C4.3928 26.1799 4.61836 26.3632 4.87674 26.4621C5.13511 26.561 5.41431 26.571 5.67787 26.4907C8.35481 25.9295 10.2741 24.1427 11.9082 21.8765C13.7834 19.2758 15.0935 16.3194 16.1258 13.2124C16.2185 12.8707 16.3822 12.558 16.6037 12.2996C16.8251 12.0413 17.0981 11.8445 17.4005 11.7251C18.5218 11.2402 19.6149 10.6746 20.719 10.1426L20.953 10.2997Z"
			fill="white"
			stroke="currentColor"
		/>
		<path
			fill-rule="evenodd"
			clip-rule="evenodd"
			d="M3.59476 12.6228C3.66264 11.5852 4.00255 10.5924 4.57242 9.76737C5.66345 8.03289 7.1218 6.75145 8.72447 5.66391C11.4303 3.82587 14.3763 2.67257 17.4678 1.94409C17.9446 1.87645 18.3847 1.62454 18.7113 1.23244C18.9697 0.927755 19.284 0.688484 19.6329 0.53088C20.3566 0.185279 20.9448 0.335686 21.3154 0.879847C21.6283 1.3378 21.6101 2.26044 21.277 2.84085C20.523 4.1562 19.3533 4.35606 18.0826 3.34255C16.2951 3.6674 14.5429 4.1989 12.8546 4.92843C10.9007 5.695 9.0501 6.75481 7.35411 8.07846C5.8243 9.30373 4.47791 10.7146 3.59476 12.6228ZM20.9269 2.02926C20.9206 1.80007 20.8412 1.58083 20.7029 1.41076C20.5646 1.24069 20.3764 1.13087 20.172 1.10093C19.5901 1.03466 18.851 1.74191 18.8105 2.40282C18.8044 2.63288 18.8797 2.85642 19.02 3.02555C19.1604 3.19467 19.3547 3.29592 19.5614 3.3076C19.8891 3.31219 20.2073 3.18558 20.458 2.9509C20.7086 2.71621 20.8751 2.3891 20.9269 2.02926Z"
			fill="white"
			stroke="currentColor"
		/>
		<path
			fill-rule="evenodd"
			clip-rule="evenodd"
			d="M16.8133 7.17825C12.7137 8.31291 8.83211 9.8944 5.62863 13.0711C5.16728 13.5311 4.74638 14.0388 4.37163 14.5876C3.99709 15.1312 3.70542 15.7458 3.3623 16.3555C3.40071 15.241 3.80039 14.2925 4.33112 13.3991C5.13863 12.0319 6.24874 10.9993 7.44266 10.0733C10.0698 8.03151 13.024 6.79356 16.098 5.88102C16.7032 5.70368 17.2486 5.52195 17.7351 5.01662C18.4416 4.28245 19.4307 4.29927 19.8637 4.91773C20.2845 5.51833 20.0948 6.64962 19.46 7.30174C18.6744 8.11772 17.9123 8.09856 16.8133 7.17825ZM18.3948 7.23443C18.9449 7.20854 19.5334 6.5396 19.5122 5.96593C19.5068 5.85258 19.4808 5.74162 19.4358 5.63971C19.3909 5.53781 19.3278 5.44707 19.2505 5.37295C19.1732 5.29884 19.0833 5.24287 18.986 5.20841C18.8888 5.17396 18.7863 5.16173 18.6846 5.17247C18.1195 5.22424 17.5412 5.88076 17.5582 6.44873C17.5642 6.56248 17.5909 6.67369 17.6368 6.7756C17.6826 6.87751 17.7466 6.96799 17.8248 7.04155C17.9031 7.11511 17.994 7.17021 18.0919 7.2035C18.1899 7.23679 18.293 7.24758 18.3948 7.23521V7.23443Z"
			fill="white"
			stroke="currentColor"
		/>
		<path
			fill-rule="evenodd"
			clip-rule="evenodd"
			d="M15.302 10.7494C10.8047 12.452 6.4113 14.2401 3.51276 18.8825C3.57929 18.4712 3.67447 18.0663 3.79744 17.6715C4.38684 16.1506 5.39918 15.0079 6.5498 14.0022C8.77027 12.0582 11.3094 10.7921 13.9577 9.76511C14.7913 9.44177 15.6814 9.28463 16.3425 8.5023C16.5443 8.26672 16.9733 8.1857 17.3004 8.18363C18.022 8.17793 18.455 8.92117 18.241 9.6978C17.8544 11.0957 16.8281 11.5925 15.6665 10.9448C15.5743 10.8943 15.4817 10.8459 15.302 10.7494ZM17.7322 9.48785C17.7283 9.38383 17.7056 9.28176 17.6653 9.18775C17.6251 9.09374 17.5682 9.00973 17.4981 8.94076C17.428 8.8718 17.3461 8.81928 17.2573 8.78638C17.1684 8.75347 17.0746 8.74085 16.9813 8.74927C16.7301 8.80501 16.5005 8.94546 16.3237 9.1515C16.1469 9.35754 16.0315 9.61916 15.9931 9.90076C15.9931 10.0042 16.0116 10.1066 16.0477 10.2019C16.0837 10.2972 16.1365 10.3836 16.203 10.456C16.2694 10.5283 16.3482 10.5852 16.4347 10.6232C16.5212 10.6612 16.6136 10.6796 16.7066 10.6774C16.9796 10.6557 17.2356 10.522 17.4251 10.3024C17.6146 10.0827 17.724 9.79263 17.7322 9.48837V9.48785Z"
			fill="white"
			stroke="currentColor"
		/>
		<path
			fill-rule="evenodd"
			clip-rule="evenodd"
			d="M4.85522 18.3586C4.93468 18.2377 5.02066 18.1223 5.11268 18.013C5.21968 17.9196 5.33343 17.8362 5.45276 17.7637C7.21 19.1712 9.26682 19.8784 11.4014 20.3946C10.7191 21.5495 10.7 21.5542 9.54546 21.2231C8.03498 20.8213 6.61397 20.0814 5.3692 19.0485C5.20779 18.9057 5.05601 18.7499 4.91505 18.5825C4.87431 18.5377 4.87641 18.445 4.85522 18.3586Z"
			fill="white"
			stroke="currentColor"
		/>
		<path
			fill-rule="evenodd"
			clip-rule="evenodd"
			d="M9.59783 22.6898L8.57361 23.6316C6.95884 23.1491 5.50095 22.3611 4.34172 20.9815C3.88059 20.4316 3.89456 20.39 4.2528 19.5225C5.68578 21.1995 7.52774 22.0165 9.59783 22.6898Z"
			fill="white"
			stroke="currentColor"
		/>
		<path
			fill-rule="evenodd"
			clip-rule="evenodd"
			d="M7.04121 24.5355C5.72928 25.2899 5.62127 25.2697 4.75999 24.127C4.22905 23.4459 3.89094 22.6055 3.78815 21.7114C4.7018 23.0887 5.82192 23.8619 7.04121 24.5355Z"
			fill="white"
		/>
	</svg>
	{#if animation && innerWidth != undefined}
		<div class="logo-text">
			<span class="first-word" class:animation transition:typewriter>Secure </span>
			<span class="second-word" class:animation transition:typewriter={{ delay: 2000 }}
				>authorities</span
			>
		</div>
	{/if}
	{#if !animation && innerWidth != undefined}
		<div class="logo-text">
			<span class="first-word" class:animation>Secure </span>
			<span class="second-word" class:animation>authorities</span>
		</div>
	{/if}
</div>

<style lang="scss">
	@use 'src/styles/index.scss' as *;

	@media screen and (min-width: $desktop) {
		.logo {
			margin-top: 7px;
		}
	}

	.logo {
		position: static;
		width: auto;
		margin-left: 15px;

		path {
			fill: $white;
			stroke-dashoffset: 0;
			stroke: none;
		}
		&.animation {
			position: absolute;
			width: 200px;
			left: 30px;
			top: 10px;
			left: 50%;
			top: 40%;
			transform: scale(3);
			animation: scaleAndMove 3s 4s ease-in-out forwards;

			path {
				fill: transparent;
				stroke: white;
				stroke-width: 0.3;
				stroke-dasharray: 50% 50%;
				stroke-dashoffset: 50;
				animation: draw 4s linear forwards;
			}
		}

		@keyframes scaleAndMove {
			100% {
				transform: scale(1);
				left: 0px;
				top: 0px;
			}
		}
	}

	@keyframes draw {
		0% {
			fill: transparent;
		}
		50% {
			fill: rgb(255, 255, 255, 0.5);
		}
		75% {
			fill: rgb(255, 255, 255, 0.8);
		}
		100% {
			fill: $white;
			stroke-dashoffset: 0;
			stroke: none;
		}
	}

	.logo-text {
		width: auto;
		margin-left: 5px;
		font-family: 'Space Grotesk', sans-serif;
		font-optical-sizing: auto;
		font-size: 14px;
		font-weight: 400;
		line-height: 17.5px;
		text-align: left;
		color: rgba(230, 237, 250, 1);
		&.animation {
			width: 200px;
		}

		.first-word {
			position: static;
			&.animation {
				position: absolute;
				bottom: -18px;
				left: 5px;
				bottom: 0;
				left: 30px;
				animation: moveText1 1s 4.1s ease-in forwards;
			}
		}

		.second-word {
			position: static;
			&.animation {
				position: absolute;
				bottom: -33px;
				left: 5px;
				bottom: 0;
				left: 83px;
				animation: moveText2 1s 4.1s ease-in forwards;
			}
		}
		@keyframes moveText1 {
			100% {
				bottom: -18px;
				left: 5px;
			}
		}

		@keyframes moveText2 {
			100% {
				bottom: -35px;
				left: 5px;
			}
		}
	}

	@media screen and (min-width: $desktop) {
		@keyframes scaleAndMove {
			100% {
				transform: scale(1);
				left: 0px;
				top: 0px;
			}
		}
	}

	@media screen and (max-width: $desktop) {
		.logo {
			width: 50px;
			margin-top: 13px;
		}
	}

	@media screen and (max-width: $tablet) {
		.logo {
			width: 50px;
			margin-top: 13px;
			&.animation {
				top: 40%;
				left: 35%;
				transform: scale(1.8);
			}
		}
	}
</style>
