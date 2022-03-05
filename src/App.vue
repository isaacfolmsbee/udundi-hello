<script setup>
import FacebookIcon from './components/icons/IconFacebook.vue'
import InstagramIcon from './components/icons/IconInstagram.vue'
import PlusIcon from './components/icons/IconPlus.vue'
import { reactive } from 'vue';
import anime from 'animejs';

const state = reactive({ isDetailsOpen: false, isSlideEnabled: true });

const roundedPath = "M41.4988 46.0003C168.5 -11.4999 275.5 -18.5 418.999 46.0003C483 175.5 478.5 294 418.999 441.5C300.5 497 153 494.5 41.4988 441.5C-9.99984 285.5 -16.5 193 41.4988 46.0003Z";
const nearlySquarePath = "M5.49861 4.99993C196.5 -0.999969 196.5 -0.999986 382.999 4.99993C390 181.5 389 197.5 382.999 400.5C201.5 405 174 409 5.49861 400.5C-2 214 -0.499968 188 5.49861 4.99993Z";
const squarePath = "M0.498537 0.000244141C122.5 0.000328064 239 0.000282288 377.999 0.000244141C377.999 127 377.999 254 377.999 395.5C260.5 395.5 135.5 395.5 0.498537 395.5C0.498502 252.5 0.498964 131.5 0.498537 0.000244141Z";

function toggleDetails() {
	state.isDetailsOpen = !state.isDetailsOpen;
	state.isSlideEnabled = false;

	if (state.isDetailsOpen) {
		anime({
			targets: '#details-pane path',
			d: [
				{ value: roundedPath },
				{ value: nearlySquarePath },
				{ value: squarePath },

			],
			easing: 'cubicBezier(0.080, 0.165, 0.000, 0.550)',
			delay: 80,
			duration: 530,
			loop: false
		});
	}
}
</script>

<template>
	<div class="header">
		<h1
			:class="[state.isSlideEnabled ? 'slide-in' : state.isDetailsOpen ? 'fade-right' : 'fade-left']"
			class="title"
			id="title"
		>Explore</h1>
		<div class="sub-header">
			<svg
				id="details-pane"
				class="details-pane"
				:class="{ open: state.isDetailsOpen }"
				viewBox="0 0 535 531"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
				preserveAspectRatio="none"
			>
				<path
					d="M41.4988 46.0003C168.5 -11.4999 275.5 -18.5 418.999 46.0003C483 175.5 478.5 294 418.999 441.5C300.5 497 153 494.5 41.4988 441.5C-9.99984 285.5 -16.5 193 41.4988 46.0003Z"
					fill="#FFFFFF"
				/>
			</svg>
			<div class="details-container" :class="{ 'show-details': state.isDetailsOpen }">
				<svg @click="toggleDetails" viewBox="0 0 22 22" fill="none" xmlns="http://www.w3.org/2000/svg">
					<path
						d="M10.9591 8.92561L19.5575 0L21.7692 2.12599L13.1094 10.7331L22 19.358L19.6977 21.7877L11.225 13.0803L2.56813 22L0.189907 19.7059C3.11155 16.8074 5.95139 14.0091 8.87012 11.1283L0 2.4238L2.27888 0L10.9591 8.92561Z"
						fill="#611818"
					/>
				</svg>
				<h3>Explore</h3>
				<hr />
				<p class="info">
					Sed ut perspiciatis unde omnis iste natus error sit voluptatem
					accusantium doloremque laudantium, totam rem aperiam, eaque
					ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae
					dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas
					sit aspernatur aut odit aut fugit, sed quia consequuntur magni
					dolores eos qui ratione voluptatem sequi nesciunt. Neque porro
					quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur,
					adipisci velit, sed quia non numquam eius modi tempora incidunt ut
					labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad
					minima veniam, quis nostrum exercitationem ullam corporis suscipit
					laboriosam, nisi ut aliquid ex ea commodi consequatur?
				</p>
				<button class="button">READ MORE</button>
			</div>
			<PlusIcon
				@click="toggleDetails"
				:class="{ 'button-activate': state.isDetailsOpen }"
				class="icon plus-icon"
			/>
			<h5 class="subtitle">More Details</h5>
		</div>
	</div>
	<div class="backdrop"></div>
	<div class="social">
		<FacebookIcon class="icon" />
		<InstagramIcon class="icon" />
	</div>
</template>

<style lang="scss">
@import "./assets/base.css";
@import "./assets/animations.css";

$autumn-red: #611818;

.header {
	position: fixed;
	bottom: 21%;
	left: 5%;
	z-index: 10;

	h1 {
		font-size: 68px;
		letter-spacing: 5px;
		font-family: "Playfair Display", serif;
		color: white;
		background: linear-gradient(90deg, #ffffff00 63%, white 72%);
		background-size: 400%;
		-webkit-text-fill-color: transparent;
		-webkit-background-clip: text;
		-moz-background-clip: text;
		background-clip: text;
		background-position: 100%;
	}

	.slide-in {
		animation: slide-in ease 950ms 1;
		-o-animation: slide-in ease 950ms 1;
		-moz-animation: slide-in ease 950ms 1;
		-webkit-animation: slide-in ease 950ms 1;
	}

	.fade-right {
		animation: fade-out-text 1.3s ease 1;
		-o-animation: fade-out-text 1.3s ease 1;
		-moz-animation: fade-out-text 1.3s ease 1;
		-webkit-animation: fade-out-text 1.3s ease 1;
		background-position: 0%;
	}

	.fade-left {
		animation: fade-in-text 1s ease 1;
		-o-animation: fade-in-text 1s ease 1;
		-webkit-animation: fade-in-text 1s ease 1;
		-moz-animation: fade-in-text 1s ease 1;
		background-position: 100%;
	}

	.sub-header {
		margin-left: 12px;
		display: flex;

		.details-pane {
			position: absolute;
			z-index: 20;
			left: 6px;
			bottom: 10px;
			height: 0px;
			width: 0px;
			transition: all 400ms ease;
			-o-transition: all 400ms ease;
			-moz-transition: all 400ms ease;
			-webkit-transition: all 400ms ease;
			transition-delay: 173ms;
			-o-transition-delay: 173ms;
			-moz-transition-delay: 173ms;
			-webkit-transition-delay: 173ms;
			max-width: 500px;
			filter: drop-shadow(0px 0px 8px rgba(0, 0, 0, 0.644));
		}

		.open {
			bottom: -30vh;
			height: 95vh;
			width: 114vw;
		}

		.details-container {
			visibility: hidden;
			display: flex;
			flex-direction: column;
			opacity: 0;
			transition: all ease 300ms;
			-o-transition: all ease 300ms;
			-moz-transition: all ease 300ms;
			-webkit-transition: all ease 300ms;
			left: -4%;
			z-index: 20;
			position: absolute;
			bottom: 0;
			height: 65vh;
			width: 84vw;
			max-width: 360px;
			padding: 20px 28px;

			svg {
				cursor: pointer;
				position: absolute;
				top: 2%;
				right: 5.5%;
				height: 19px;
				width: 19px;
			}

			h3 {
				letter-spacing: 1.6px;
				font-family: "Playfair Display", serif;
				color: $autumn-red;
				font-size: 28px;
				margin-bottom: 5px;
			}

			hr {
				margin: 0;
				height: 2px;
				width: 65%;
				background: transparent;
				background-image: linear-gradient(to right, $autumn-red, #61181800);
				opacity: 100%;
			}

			p {
				margin-top: 14px;
				margin-bottom: 8px;
				letter-spacing: 0.3px;
				line-height: 24px;
				font-family: "Open Sans", sans-serif;
				color: #505050;
				font-size: 10px;
			}

			button {
				padding: 6px 32px;
				margin: auto auto auto 0;
				font-family: "Open Sans", sans-serif;
				color: white;
				font-size: 14px;
				border: 1px solid #979797;
				background-image: linear-gradient(to right, $autumn-red, #a36754);
			}
		}

		.show-details {
			animation: reveal-details ease 800ms 1;
			-o-animation: reveal-details ease 800ms 1;
			-moz-animation: reveal-details ease 800ms 1;
			-webkit-animation: reveal-details ease 800ms 1;
			opacity: 100%;
			left: 0%;
			visibility: visible;
		}

		.plus-icon {
			height: 24px;
			width: 24px;
			position: absolute;
			transition: all ease 400ms;
			transition-delay: 400ms;
			opacity: 100;
		}

		.button-activate {
			animation: push-button ease-out 195ms 1;
			-o-animation: push-button ease-out 195ms 1;
			-moz-animation: push-button ease-out 195ms 1;
			-webkit-animation: push-button ease-out 195ms 1;
			transition-delay: 195ms;
			-o-transition-delay: 195ms;
			-moz-transition-delay: 195ms;
			-webkit-transition-delay: 195ms;
			transition-duration: 0ms;
			-o-transition-duration: 0ms;
			-moz-transition-duration: 0ms;
			-webkit-transition-duration: 0ms;
			opacity: 0;
		}

		.subtitle {
			margin-top: 2px;
			margin-left: 32px;
			font-family: "Open Sans", sans-serif;
			font-size: 14px;
		}
	}
}

.backdrop {
	position: fixed;
	width: 140vw;
	height: 50vh;
	top: 68vh;
	right: 0;
	transform: rotate(23deg);
	background-color: $autumn-red;
}

.social {
	width: 120px;
	height: 53px;
	position: fixed;
	bottom: 5%;
	left: auto;
	right: 6%;
	display: flex;
	align-items: center;
	justify-content: space-between;

	.icon {
		filter: drop-shadow(2px 2px 3px rgb(0 0 0 / 0.5));
	}
}

.icon {
	cursor: pointer;
}

@media screen and (min-width: 648px) {
	.header {
		left: 60px;

		h1 {
			font-size: 128px;
			letter-spacing: 5.6px;
		}

		.sub-header {
			.open {
				bottom: -200px;
				height: 700px;
				width: 500px;
			}

			.details-container {
				max-width: unset;
				bottom: -30px;
				height: 530px;
				width: 370px;
				padding: 20px 28px;

				p {
					letter-spacing: 0.3px;
					line-height: 26px;
					font-size: 11px;
				}

				h3 {
					font-size: 38px;
				}
			}

			.subtitle {
				margin-top: 0px;
				margin-left: 32px;
				font-size: 18px;
			}
		}
	}

	.backdrop {
		width: 220px;
		height: 100vh;
		top: 0%;
		left: 0%;
		transform: rotate(180deg);
	}

	.social {
		width: 75px;
		height: 120px;
		position: fixed;
		bottom: 3%;
		right: 1%;
		flex-direction: column;
		justify-items: space-between;

		.icon {
			height: 52px;
			width: 52px;
		}
	}
}

@media screen and (min-width: 1024px) {
	.header {
		left: 140px;

		h1 {
			font-size: 224px;
		}

		.sub-header {
			margin-top: -12px;
			margin-left: 50px;

			.details-pane {
				max-width: unset;
				left: 20px;
				bottom: 20px;
			}

			.open {
				left: -50px;
				bottom: -300px;
				height: 950px;
				width: 820px;
			}

			.details-container {
				margin-left: -50px;
				bottom: -60px;
				height: 710px;
				width: 580px;
				padding: 62px 62px;

				button {
					padding: 14px 58px;
					font-size: 18px;
					letter-spacing: 1.7px;
				}

				p {
					margin-top: 20px;
					letter-spacing: 0.36px;
					line-height: 30px;
					font-size: 14px;
				}

				hr {
					margin-top: 20px;
				}

				h3 {
					font-size: 66px;
				}

				svg {
					top: 3.5%;
					right: 4.5%;
					height: 22px;
					width: 22px;
				}
			}

			.button-activate {
				animation: push-button-large ease-out 200ms;
				-o-animation: push-button-large ease-out 200ms;
				-moz-animation: push-button-large ease-out 200ms;
				-webkit-animation: push-button-large ease-out 200ms;
			}

			.plus-icon {
				margin-top: -3px;
				height: 43px;
				width: 43px;
			}

			.subtitle {
				margin-left: 56px;
				font-size: 25px;
				letter-spacing: 0.63px;
			}
		}
	}

	.backdrop {
		width: 413px;
	}

	.social {
		height: 160px;

		.icon {
			height: 68px;
			width: 68px;
		}
	}
}
</style>
