<script setup lang="ts">
import { useToggle } from '@vueuse/core'

import IconCart from './icons/IconCart.vue'
import IconBurger from './icons/IconBurger.vue'
import { AppNav, AppPhone, AppLogo, MobileMenu } from '.'
import { useBodyScrollLock } from '@/composables/useBodyScrollLock'

const items = [
	{
		text: 'Каталог',
		sub: [
			{ text: 'Ёжики' },
			{ text: 'Питание' },
			{ text: 'переноски' },
			{ text: 'Лекарства' },
		],
	},
	{ text: 'о\xa0нас' },
	{ text: 'контакты' },
	{ text: 'галерея' },
]

const [mobileMenuVisible, toggleMobileMenuVisible] = useToggle(false)

useBodyScrollLock(mobileMenuVisible)
</script>

<template>
	<mobile-menu
		:is-visible="mobileMenuVisible"
		@close-menu="toggleMobileMenuVisible(false)"
	></mobile-menu>

	<header class="header">
		<div class="container">
			<div class="content">
				<div class="burger">
					<button class="burger-btn" @click="toggleMobileMenuVisible(true)">
						<icon-burger class="burger-icon" width="25" height="14"></icon-burger>
					</button>
				</div>
				<div class="logo">
					<app-logo></app-logo>
				</div>
				<div class="nav">
					<app-nav :nav-items="items"></app-nav>
				</div>
				<div class="phone">
					<app-phone with-icon hide-text-mobile></app-phone>
				</div>
				<div class="cart-wrapper">
					<a class="cart" href="#">
						<span class="count">1</span>
						<icon-cart class="cart-icon" width="36" height="32"></icon-cart>
					</a>
				</div>
			</div>
		</div>
	</header>
</template>

<style scoped>
.header {
	--min-h-header: 145px;
	--cart-h: 32px;
	--cart-w: 36px;
	--cart-ml: 80px;
	--logo-h: 56px;
	--logo-w: 120px;

	position: absolute;
	top: 0;
	left: 0;
	z-index: 100;
	width: 100%;
}
.content {
	display: flex;
	align-items: center;
	min-height: var(--min-h-header);
	position: relative;
}
.burger {
	display: none;
}
.logo {
	margin-right: auto;
}
.nav {
	margin-right: 130px;
	margin-left: 25px;
}
.cart-wrapper {
	margin-left: var(--cart-ml);
}
.cart {
	position: relative;
	display: block;
	width: var(--cart-w);
	height: var(--cart-h);
}
.count {
	position: absolute;
	top: -5px;
	right: -5px;
	z-index: 1;
	background-color: #ffedcd;
	font-family: var(--ff-sec);
	font-weight: 700;
	font-size: 10px;
	line-height: 12px;
	text-transform: uppercase;
	padding: 4px 6px;
	border-radius: 50%;
	display: flex;
	align-items: center;
	justify-content: center;
	line-height: 1;
}
.cart-icon {
	width: var(--cart-w);
	height: var(--cart-h);
}

@media (max-width: 1300px) {
	.header {
		--cart-ml: 30px;
	}
	.nav {
		margin: 0 25px;
	}
}
@media (max-width: 576px) {
	.header {
		--min-h-header: 80px;
		--cart-h: 26px;
		--cart-w: 32px;
		--cart-ml: 12px;
	}
	.burger {
		display: block;
		margin-right: auto;
	}
	.burger-btn {
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 15px;
		margin-left: -15px;
	}
	.logo {
		position: absolute;
		top: 50%;
		left: 50%;
		z-index: 1;
		transform: translate(-50%, -50%);
	}
	.nav {
		display: none;
	}
	.count {
		font-size: 8px;
		line-height: 9px;
		padding: 2px 4px;
	}
}
</style>
