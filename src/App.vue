<script setup>
import FacebookIcon from './components/icons/IconFacebook.vue'
import InstagramIcon from './components/icons/IconInstagram.vue'
import PlusIcon from './components/icons/IconPlus.vue'
import { reactive } from 'vue';
import anime from 'animejs';

const state = reactive({ isDetailsOpen: false, isSlideEnabled: true });

const squarePath = "M61.5001 25.0003L118.835 3.2893C146.137 -7.04896 156.002 18.5942 159.783 58.9798C174.571 216.968 273.46 228.196 373.683 105.175L439 25.0003C505.169 138.299 509.944 277.274 451.707 394.847L439 420.5L372.044 443.935C292.414 471.806 205.65 471.626 126.136 443.425L61.5001 420.5L47.7309 396.641C-19.3639 280.38 -14.0139 135.978 61.5001 25.0003Z";
const roundedPath = "M61.5001 46L118.835 24.289C202.742 -7.4835 295.334 -7.68557 379.379 23.7204L439 46C505.169 159.299 509.944 298.274 451.707 415.847L439 441.5L372.044 464.935C292.414 492.805 205.65 492.625 126.136 464.424L61.5001 441.5L47.7309 417.641C-19.3639 301.379 -14.0139 156.978 61.5001 46Z";

function toggleDetails() {
	state.isDetailsOpen = !state.isDetailsOpen;
	state.isSlideEnabled = false;
	const roundedPath = "M41.4988 46.0003C168.5 -11.4999 275.5 -18.5 418.999 46.0003C483 175.5 478.5 294 418.999 441.5C300.5 497 153 494.5 41.4988 441.5C-9.99984 285.5 -16.5 193 41.4988 46.0003Z";
	const nearlySquarePath = "M5.49861 4.99993C196.5 -0.999969 196.5 -0.999986 382.999 4.99993C390 181.5 389 197.5 382.999 400.5C201.5 405 174 409 5.49861 400.5C-2 214 -0.499968 188 5.49861 4.99993Z";
	const squarePath = "M0.498537 0.000244141C122.5 0.000328064 239 0.000282288 377.999 0.000244141C377.999 127 377.999 254 377.999 395.5C260.5 395.5 135.5 395.5 0.498537 395.5C0.498502 252.5 0.498964 131.5 0.498537 0.000244141Z";

	if (state.isDetailsOpen) {
		anime({
			targets: '#details-pane path',
			d: [
				{ value: nearlySquarePath },
				{ value: squarePath },

			],
			easing: 'linear',
			delay: 250,
			duration: 325,
			loop: false
		});
	} else {
		anime({
			targets: '#details-pane path',
			d: [
				{ value: roundedPath },
			],
			easing: 'liner',
			delay: 400,
			duration: 0,
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
			<PlusIcon
				@click="toggleDetails"
				:class="{ 'button-activate': state.isDetailsOpen }"
				class="icon plus-icon fade-in"
			/>
			<h5 class="subtitle fade-in">More Details</h5>
		</div>
	</div>
	<div class="backdrop"></div>
	<div class="social">
		<FacebookIcon class="icon fade-in" />
		<InstagramIcon class="icon fade-in" />
	</div>
</template>

<style>
@import "./assets/base.css";

.details-pane {
	position: absolute;
	left: 6px;
	bottom: 10px;
	height: 0px;
	width: 0px;
	transition: all 400ms ease;
	transition-delay: 150ms;
}

.open {
	bottom: -30vh;
	height: 100vh;
	width: 110vw;
}

.header {
	position: fixed;
	bottom: 21%;
	left: 5%;
	z-index: 10;
}

.sub-header {
	margin-left: 12px;
	display: flex;
}

.title {
	font-size: 68px;
	letter-spacing: 5px;
	font-family: "Playfair Display", serif;
	color: #ffffff;
	background: linear-gradient(90deg, #ffffff00 63%, #ffffff 72%);
	background-size: 400%;
	-webkit-text-fill-color: transparent;
	-webkit-background-clip: text;
	background-clip: text;
	background-position: 100%;
}

.slide-in {
	animation: slide-in ease 950ms 1;
}

.fade-right {
	animation: fade-out-text 1.3s ease 1;
	-webkit-animation: fade-out-text 1.3s ease 1;
	-moz-animation: fade-out-text 1.3s ease 1;
	background-position: 0%;
}

.fade-left {
	animation: fade-in-text 1s ease 1;
	-webkit-animation: fade-in-text 1s ease 1;
	-moz-animation: fade-in-text 1s ease 1;
	background-position: 100%;
}

.subtitle {
	margin-top: 2px;
	margin-left: 32px;
	font-family: "Open Sans", sans-serif;
	font-size: 14px;
}

.backdrop {
	position: fixed;
	width: 140vw;
	height: 50vh;
	top: 68vh;
	right: 0;
	transform: rotate(23deg);
	background-color: #611818;
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
}

.icon {
	cursor: pointer;
}

.plus-icon {
	position: absolute;
}

.social .icon {
	filter: drop-shadow(2px 2px 3px rgb(0 0 0 / 0.5));
}

.button-activate {
	transition: all;
	transition-duration: 340ms;
	transition-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1.275);
	height: 16px;
	width: 16px;
	margin-top: 4px;
	margin-left: 4px;
}

.fade-in {
	animation: fade-in ease 1050ms;
	animation-iteration-count: 1;
}

@keyframes fade-in {
	0% {
		opacity: 0;
	}
	100% {
		opacity: 1;
	}
}

@keyframes slide-in {
	0% {
		transform: translateX(40px);
	}
	100% {
		transform: translateX(0px);
	}
}

@keyframes fade-out-text {
	0% {
		background-position: 100% 100%;
	}
	10% {
		background-position: 100% 100%;
	}
	100% {
		background-position: 0% 100%;
	}
}

@-webkit-keyframes fade-out-text {
	0% {
		background-position: 100% 100%;
	}
	100% {
		background-position: 0% 100%;
	}
}

@keyframes fade-in-text {
	0% {
		background-position: 0% 100%;
	}
	100% {
		background-position: 100% 100%;
	}
}

@-webkit-keyframes fade-in-text {
	0% {
		background-position: 0% 100%;
	}
	100% {
		background-position: 100% 100%;
	}
}
</style>
