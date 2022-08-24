<script setup lang="ts">
import { computed } from 'vue'
import IconHedgehog from './icons/IconHedgehog.vue'
import IconSyringe from './icons/IconSyringe.vue'
import IconHeart from './icons/IconHeart.vue'

type Variants = 1 | 2 | 3

const props = defineProps<{
	title: string
	color: Variants
	icon: Variants
}>()

const _color = computed(() => ['color-1', 'color-2', 'color-3'][props.color - 1])
const _icon = computed(() => [IconHedgehog, IconSyringe, IconHeart][props.icon - 1])
</script>

<template>
	<div class="benefit">
		<div class="icon-wrapper" :class="_color">
			<component class="icon" :is="_icon"></component>
		</div>
		<div class="text">
			<div class="title">{{ title }}</div>
			<div class="desc">
				<slot></slot>
			</div>
		</div>
	</div>
</template>

<style scoped>
.benefit {
	display: grid;
	justify-items: center;
	padding: 6px;
}
.icon-wrapper {
	box-shadow: var(--bx-sh-prim);
	width: 152px;
	height: 152px;
	display: flex;
	align-items: center;
	justify-content: center;
	margin-bottom: 30px;
	border-radius: 50%;
}
.icon-wrapper.color-1 {
	background-color: #ffedcd;
}
.icon-wrapper.color-2 {
	background-color: #e2f0df;
}
.icon-wrapper.color-3 {
	background-color: #94afab;
}
.text {
	text-align: center;
}
.title {
	font-weight: 700;
	font-size: 16px;
	line-height: 19px;
	text-transform: uppercase;
	margin-bottom: 8px;
	color: var(--c-sec);
}
.desc {
	font-family: var(--ff-sec);
	font-size: 14px;
	line-height: 22px;
	color: var(--c-sec);
	font-weight: 400;
}

@media (max-width: 576px) {
	.benefit {
		justify-items: left;
	}
	.icon-wrapper {
		width: 92px;
		height: 92px;
		margin-bottom: 18px;
	}
	.icon {
		max-width: 43px;
	}
	.text {
		text-align: left;
	}
	.title {
		font-size: 14px;
		line-height: 18px;
	}
	.desc {
		font-size: 10px;
		line-height: 159%;
	}
}
</style>
