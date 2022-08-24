<script setup lang="ts">
import { AppNav, AppPhone, AppLogo, FadeTransition } from '.'
import IconClose from './icons/IconClose.vue'

interface Props {
	isVisible: boolean
}

defineProps<Props>()
defineEmits<{
	(e: 'close-menu'): void
}>()

const items = [
	{ text: 'Каталог' },
	{ text: 'о\xa0нас' },
	{ text: 'контакты' },
	{ text: 'галерея' },
]
</script>

<template>
	<Teleport to="body">
		<fade-transition>
			<div class="mobile-menu" v-if="isVisible">
				<div class="mobile-menu__header">
					<button class="close" @click="$emit('close-menu')">
						<IconClose />
					</button>
					<div class="logo">
						<app-logo></app-logo>
					</div>
				</div>

				<div class="mobile-menu__nav">
					<app-nav :nav-items="items" col-mobile></app-nav>
				</div>

				<div class="mobile-menu__phone">
					<app-phone></app-phone>
				</div>
			</div>
		</fade-transition>
	</Teleport>
</template>

<style scoped lang="scss">
.mobile-menu {
	display: flex;
	flex-direction: column;

	position: absolute;
	top: 0;
	left: 0;
	z-index: 11111;

	width: 95%;
	height: 90vh;
	padding: 20px 0 43px 0;
	overflow: hidden;
	border-radius: 0px 10px 10px 0px;
	background-color: #ffffff;
	box-shadow: 4px 4px 20px #e3e3e3;

	&__header {
		display: flex;
		align-items: center;
		position: relative;
		margin-bottom: 56px;
		padding: 0 20px;
	}
	&__nav {
		margin-bottom: 15px;
		padding: 0 40px;
	}
	&__phone {
		margin-top: auto;
		padding: 0 40px;
	}
}
.close {
	padding: 10px;
	margin-left: -10px;
	display: flex;
	align-items: center;
	justify-content: center;
}
.logo {
	position: absolute;
	top: 50%;
	left: 50%;
	z-index: 1;
	transform: translate(-50% /* X */, -50% /* Y */);
}
</style>
