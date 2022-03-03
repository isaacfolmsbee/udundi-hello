<script setup>
import FacebookIcon from './components/icons/IconFacebook.vue'
import InstagramIcon from './components/icons/IconInstagram.vue'
import PlusIcon from './components/icons/IconPlus.vue'
</script>

<template>
	<div class="header">
		<h1 class="title">Explore</h1>
		<div class="sub-header">
			<PlusIcon class="icon ease-in" />
			<h5 class="subtitle ease-in">More Details</h5>
		</div>
	</div>
	<div class="backdrop"></div>
	<div class="social">
		<FacebookIcon class="icon ease-in" />
		<InstagramIcon class="icon ease-in" />
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
	animation: slide-in ease 950ms;
	animation-iteration-count: 1;
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

.ease-in {
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
</style>
