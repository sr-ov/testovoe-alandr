<script setup lang="ts">
import { ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Swiper as SwiperClass } from 'swiper'
import 'swiper/css'

import { AppCard } from '.'
import IconArrowLeft from './icons/IconArrowLeft.vue'
import IconArrowRight from './icons/IconArrowRight.vue'
import img1 from '@/assets/images/slides/01.png'
import img2 from '@/assets/images/slides/02.png'

const items = [
	{
		title: 'Ежик “Евгений”',
		desc: 'Очень любит сладости. Маленький сладкоежка=) Мы называем его так между собой. Ручной, любит внимаение ',
		sale: 50,
		imgSrc: img1,
		bgc: 'rgba(255, 237, 205, 1)',
		price: {
			old: 3000,
			new: 1500,
		},
	},
	{
		title: 'Ежик “Максим”',
		desc: 'Немного игривый и задорный характер этого друга никого не оставит равнодушным!',
		sale: 50,
		imgSrc: img2,
		bgc: 'rgba(225, 240, 222, 1)',
		price: {
			old: 5000,
			new: 2500,
		},
	},
	{
		title: 'Ежик “Евгений”',
		desc: 'Очень любит сладости. Маленький сладкоежка=) Мы называем его так между собой. Ручной, любит внимаение ',
		sale: 50,
		imgSrc: img1,
		bgc: 'rgba(255, 237, 205, 1)',
		price: {
			old: 3000,
			new: 1500,
		},
	},
	{
		title: 'Ежик “Максим”',
		desc: 'Немного игривый и задорный характер этого друга никого не оставит равнодушным!',
		sale: 50,
		imgSrc: img2,
		bgc: 'rgba(225, 240, 222, 1)',
		price: {
			old: 5000,
			new: 2500,
		},
	},
]
const swiper = ref<SwiperClass | null>(null)
const modules = [Autoplay]

const onSwiper = (sw: SwiperClass) => {
	swiper.value = sw
}
const breakpoints = {
	992: {
		slidesPerView: 2,
	},
}
</script>

<template>
	<div class="slider">
		<div class="slider-container container">
			<button
				class="button button-prev"
				:disabled="swiper?.isBeginning"
				@click="swiper?.slidePrev()"
			>
				<icon-arrow-left></icon-arrow-left>
			</button>
			<button
				class="button button-next"
				:disabled="swiper?.isEnd"
				@click="swiper?.slideNext()"
			>
				<icon-arrow-right></icon-arrow-right>
			</button>

			<div class="container-sm container-sm--px0">
				<Swiper
					class="slider-content"
					@swiper="onSwiper"
					slidesPerView="auto"
					:space-between="5"
					:modules="modules"
					:breakpoints="breakpoints"
				>
					<SwiperSlide v-for="{ desc, bgc, ...item } in items">
						<div class="slide-wrapper">
							<app-card :style="{ '--bgc': bgc }" v-bind="item">
								{{ desc }}
							</app-card>
						</div>
					</SwiperSlide>
				</Swiper>
			</div>
		</div>
	</div>
</template>

<style scoped lang="scss">
.slider-container {
	max-width: 1380px;
	position: relative;
}
.swiper-slide {
	height: auto;
	transform: initial;

	@media (max-width: 576px) /* mobile */ {
		width: 95%;
	}
}
.slide-wrapper {
	padding-top: 20px;
	height: 100%;
	padding-right: 20px;

	@media (max-width: 576px) /* mobile */ {
	}
}
.button {
	display: flex;
	align-items: center;
	justify-content: center;
	padding: 10px;

	position: absolute;
	top: 50%;
	transform: translate(-50% /* X */, 0 /* Y */);
	z-index: 1;

	&:disabled {
		opacity: 0.5;
	}

	@media (max-width: 991px) {
		display: none;
	}
}
.button-prev {
	left: 0;
}
.button-next {
	right: 0;
}
</style>
