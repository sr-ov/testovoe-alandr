<script setup lang="ts">
import IconTheTitle from './icons/IconTheTitle.vue'
import { AppButton, AppBenefit } from '.'

interface Props {}

// defineProps<Props>()
</script>

<template>
	<div class="hero">
		<img
			class="hero-decor decor-1"
			src="@/assets/images/hero/decor-1.svg"
			alt=""
			aria-hidden="true"
		/>
		<img
			class="hero-decor decor-2"
			src="@/assets/images/hero/decor-2.svg"
			alt=""
			aria-hidden="true"
		/>

		<div class="hero-container container">
			<div class="content">
				<div class="text">
					<h1 class="title">
						<icon-the-title class="title-icon"></icon-the-title>
					</h1>
					<h2 class="subtitle">тоже любят молоко</h2>
					<p class="desc">
						Заведите себе ёжика. Он всегда выслушает, не будет мяукать в 5 утра и
						царапать вашу мебель.
					</p>
					<div class="btn-wrapper">
						<app-button class="btn">Купить ёжика</app-button>
					</div>
				</div>

				<img
					class="img img-1 events-none"
					src="@/assets/images/hero/01.png"
					alt="ёж"
				/>

				<div class="benefits">
					<img
						class="img benefits-img events-none"
						src="@/assets/images/hero/02.png"
						alt="ёж"
					/>

					<div class="benefits-wrapper">
						<div class="benefits-item benefits-item-pt">
							<app-benefit title="разведение ежиков" :icon="1" :color="1">
								Собственная ферма, уход и содержание
							</app-benefit>
						</div>
						<div class="benefits-item">
							<app-benefit title="здоровье" :icon="2" :color="2">
								Всегда прививаем и вовремя обследуем ваших будущих питомцев
							</app-benefit>
						</div>
						<div class="benefits-item benefits-item-pt">
							<app-benefit title="любовь и забота" :icon="3" :color="3">
								любовь и забота
							</app-benefit>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped>
.hero {
	padding-bottom: 20px;
	position: relative;
}
.hero-decor {
	position: absolute;
	z-index: 1;
	pointer-events: none;
}
.decor-1 {
	top: 0;
	left: 0;
}
.decor-2 {
	bottom: 0;
	right: 0;
}
.hero-container {
	max-width: 1920px;
	padding: 0;
}
.content {
}
.text {
	text-align: center;
	max-width: 630px;
	margin: 0 auto;
	padding: 290px 15px 35px 15px;
	z-index: 20;
}
.title {
	margin-bottom: 20px;
}
.subtitle {
	font-weight: 400;
	font-size: 50px;
	line-height: 61px;
	text-transform: uppercase;
	color: var(--c-prim);
	margin-bottom: 18px;
}
.desc {
	font-weight: 400;
	font-size: 14px;
	line-height: 16px;
	color: var(--c-prim);
	margin-bottom: 34px;
	font-family: var(--ff-sec);
}
.btn-wrapper {
	display: flex;
	justify-content: center;
}
.btn {
	min-width: 328px;
	min-height: 70px;
}

.img {
	position: absolute;
	z-index: 10;
}
.img-1 {
	left: 0;
	bottom: -50px;
}

.benefits {
	position: relative;
	overflow: hidden;
	padding-top: 95px;
}
.benefits::after {
	content: '';
	position: absolute;
	top: 85px;
	left: 50%;
	z-index: 1;
	transform: translate(-50%, 0);
	height: 1920px;
	width: calc(1920px * 2);
	border-radius: 50%;
	box-shadow: inset 0px 4px 4px rgba(0, 0, 0, 0.25);
	pointer-events: none;
}
.benefits-img {
	right: 0;
	bottom: 0;
}
.benefits-wrapper {
	max-width: 874px;
	margin: 0 auto;
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	column-gap: 155px;
	padding-left: 15px;
	padding-right: 15px;
}
.benefits-item {
	z-index: 10;
}
.benefits-item-pt {
	padding-top: 25px;
}

@media (max-width: 1700px) {
	.img-1 {
		bottom: 20%;
		transform: translate(0, 20%);
	}
}
@media (max-width: 991px) {
	.img-1 {
		display: none;
	}
	.benefits::after {
		display: none;
	}
	.benefits-img {
		right: 0;
		top: 0;
		bottom: initial;
	}
	.benefits-item-pt {
		padding-top: 0;
	}
	.benefits-wrapper {
		grid-template-areas:
			'tl .'
			'bl br';
		grid-template-rows: repeat(2, 1fr);
		grid-template-columns: repeat(2, 1fr);
		gap: 30px;
	}
	.benefits-item:nth-child(1) {
		grid-area: tl;
	}
	.benefits-item:nth-child(2) {
		grid-area: bl;
	}
	.benefits-item:nth-child(3) {
		grid-area: br;
	}
}

@media (max-width: 576px) {
	.title {
		height: 44px;
		width: auto;
	}
	.title-icon {
		height: 44px;
		width: auto;
	}
	.subtitle {
		font-size: 24px;
		line-height: 29px;
		margin-bottom: 7px;
	}
	.desc {
		font-size: 12px;
		line-height: 146%;
		margin-bottom: 21px;
	}
}

@media (max-width: 480px) {
	.text {
		text-align: left;
		padding-top: 90px;
		padding-bottom: 50px;
	}
	.btn {
		min-width: 100%;
		min-height: 60px;
	}
}

@media (max-width: 360px) {
	.benefits {
		padding-top: 20px;
	}
}
</style>
