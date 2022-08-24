<script setup lang="ts">
import IconPhone from './icons/IconPhone.vue'

defineProps<{
	withIcon?: boolean
	textWhite?: boolean
	hideTextMobile?: boolean
}>()
</script>

<template>
	<a class="phone" href="tel:+79655698998">
		<span class="icon-wrapper" v-if="withIcon">
			<icon-phone class="icon"></icon-phone>
		</span>
		<span
			class="number"
			:class="{ white: textWhite, 'hide-text-mobile': hideTextMobile }"
			>+7 (965) 569-89-98</span
		>
	</a>
</template>

<style scoped>
.phone {
	display: flex;
	align-items: center;
	gap: 20px;
	text-decoration: none;
}
.icon-wrapper {
	display: flex;
	align-items: center;
	justify-content: center;
	height: 69px;
	width: 69px;
	position: relative;
}
.icon-wrapper::after {
	content: '';
	position: absolute;
	top: 0;
	left: 0;
	bottom: 0;
	right: 0;
	z-index: 1;

	background-image: linear-gradient(1.36deg, #b0d3ce 12.29%, #ffedce 83.89%);
	box-shadow: -4px -4px 20px #ffffff, 4px 4px 20px #cfd7d3;
	border-radius: var(--bd-prim);
}
.icon {
	height: 32px;
	width: 32px;
	z-index: 10;
}
.number {
	color: var(--c-sec);
	font-family: var(--ff-sec);
	font-weight: 500;
	font-size: 22px;
	line-height: 26px;
	text-transform: uppercase;
	font-feature-settings: 'pnum' on, 'lnum' on;
	white-space: nowrap;
}
.number.white {
	color: #fff;
}

@media (max-width: 991px) {
	.number.hide-text-mobile {
		display: none;
	}
}

@media (max-width: 576px) {
	.icon-wrapper {
		height: 35px;
		width: 35px;
	}
	.icon {
		height: 13px;
		width: 13px;
	}
}
</style>
