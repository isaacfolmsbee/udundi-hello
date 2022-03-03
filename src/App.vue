<script setup>
import FacebookIcon from './components/icons/IconFacebook.vue'
import InstagramIcon from './components/icons/IconInstagram.vue'
import PlusIcon from './components/icons/IconPlus.vue'
import { reactive } from 'vue';

const state = reactive({ isDetailsOpen: false, isSlideEnabled: true });

function toggleDetails() {
	state.isDetailsOpen = !state.isDetailsOpen;
	state.isSlideEnabled = false;
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
			<PlusIcon @click="toggleDetails" class="icon fade-in" />
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
	animation: fade-out-text 1.2s ease 1;
	-webkit-animation: fade-out-text 1.2s ease 1;
	-moz-animation: fade-out-text 1.2s ease 1;
	background-position: 0%;
}

.fade-left {
	animation: fade-in-text 1s ease 1;
	-webkit-animation: fade-in-text 1s ease 1;
	-moz-animation: fade-in-text 1s ease 1;
	background-position: 100%;
}

.subtitle {
	margin: auto 0;
	font-family: "Open Sans", sans-serif;
	font-size: 14px;
	margin-left: 6px;
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

.social .icon {
	filter: drop-shadow(2px 2px 3px rgb(0 0 0 / 0.5));
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
