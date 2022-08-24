<script setup lang="ts">
import IconPlus from './icons/IconPlus.vue'
import IconInfo from './icons/IconInfo.vue'
import IconSyringe from './icons/IconSyringe.vue'
import IconHeart from './icons/IconHeart.vue'

defineProps<{
	title: string
	sale: number
	imgSrc: string
	price: {
		old: number
		new: number
	}
}>()
</script>

<template>
	<div class="card">
		<div class="sale">-{{ sale }}%</div>
		<img class="bg-img" :src="imgSrc" alt="Ёж" />
		<div class="">
			<div class="info">
				<div class="info-icon-wrapper">
					<icon-info class="info-icon"></icon-info>

					<div class="syringe-likes-wrapper">
						<div class="syringe-likes-content">
							<div class="syringe">
								<icon-syringe
									fill="currentColor"
									height="26"
									width="26"
								></icon-syringe>
								Привит
							</div>
							<div class="likes">
								<icon-heart
									fill="currentColor"
									height="22"
									width="22"
								></icon-heart>
								1235
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="text">
				<div class="title">{{ title }}</div>
				<div class="desc">
					<slot></slot>
				</div>
				<div class="price">
					<div class="old">{{ price.old }}₽</div>
					<div class="new">{{ price.new }}₽</div>
				</div>
			</div>
		</div>
		<button class="btn">
			<span class="btn-icon-wrapper">
				<icon-plus class="btn-icon"></icon-plus>
			</span>
		</button>
	</div>
</template>

<style scoped lang="scss">
.card {
	padding: 19px 28px 58px 60px;
	box-shadow: 4px 4px 40px #f1f1f1;
	border-radius: 20px;
	background-color: var(--bgc);
	position: relative;
	height: 100%;

	@media (max-width: 576px) /* mobile */ {
		padding: 20px 30px 30px 30px;
	}
}
.sale {
	display: inline-block;
	font-family: var(--ff-sec);
	font-weight: 700;
	font-size: 20px;
	line-height: 23px;
	font-feature-settings: 'pnum' on, 'lnum' on;
	padding: 6px;
	background-color: var(--c-prim);
	color: #fff;
	position: absolute;
	top: -8px;
	left: 60px;
	z-index: 1;

	@media (max-width: 576px) /* mobile */ {
		left: 30px;
		font-size: 12px;
		line-height: 14px;
	}
}
.bg-img {
	position: absolute;
	top: 0;
	right: -30px;
	z-index: 22;
	width: 100%;
	height: 100%;
	object-fit: cover;
	pointer-events: none;

	@media (max-width: 576px) /* mobile */ {
		top: initial;
		left: initial;
		bottom: 30px;
		right: -70px;
	}
	@media (max-width: 480px) {
		width: 186px;
		height: 163px;
		top: initial;
		left: initial;
		right: -30px;
	}
}
.info {
	display: flex;
	justify-content: end;

	@media (max-width: 991px) /* tablet */ {
		margin-bottom: 20px;
	}
}
.info-icon-wrapper {
	position: relative;
	display: flex;
	align-items: center;
	justify-content: center;

	@media (any-hover: hover) {
		&:hover {
			.syringe-likes-wrapper {
				opacity: 1;
				visibility: visible;
			}
		}
	}
}
.info-icon {
	width: 37px;
	height: 37px;

	@media (max-width: 991px) /* tablet */ {
		display: none;
	}
}
.syringe-likes-wrapper {
	opacity: 0;
	visibility: hidden;
	transition: opacity 0.3s, visibility 0.3s;

	display: flex;
	flex-direction: column-reverse;
	align-items: center;

	font-family: var(--ff-sec);
	font-weight: 400;
	font-size: 14px;
	line-height: 22px;
	text-transform: lowercase;
	font-feature-settings: 'pnum' on, 'lnum' on;
	color: #fff;

	position: absolute;
	bottom: 0;
	left: 0;
	z-index: 1111;
	transform: translate(-42% /* X */, 100% /* Y */);

	@media (max-width: 991px) /* tablet */ {
		position: initial;
		transform: initial;
		opacity: initial;
		visibility: initial;
		display: block;
		color: var(--c-prim);

		font-size: 10px;
		line-height: 160%;
	}

	&::after {
		content: '';
		clip-path: polygon(50% 30%, 0% 100%, 100% 100%);
		background-color: var(--c-sec);
		height: 20px;
		width: 40px;
		transform: translate(0 /* X */, 1px /* Y */);

		@media (max-width: 991px) /* tablet */ {
			display: none;
		}
	}
}
.syringe-likes-content {
	display: flex;
	align-items: center;
	gap: 30px;
	background-color: var(--c-sec);
	padding: 28px;

	@media (max-width: 991px) /* tablet */ {
		padding: initial;
		background-color: initial;
		gap: 16px;

		svg {
			width: 12px;
			height: 12px;
		}
	}
}
.syringe,
.likes {
	display: flex;
	align-items: center;
	gap: 4px;
}
.text {
	max-width: 204px;
	display: flex;
	flex-direction: column;
	z-index: 111;

	background: linear-gradient(90deg, var(--bgc) 50%, rgba(255, 237, 205, 0) 100%);
}
.title {
	font-weight: 700;
	font-size: 40px;
	line-height: 48px;
	color: var(--c-sec);
	margin-bottom: 17px;

	@media (max-width: 576px) /* mobile */ {
		font-size: 30px;
		line-height: 99.6%;
		margin-bottom: 10px;
	}
}
.desc {
	font-family: var(--ff-sec);
	font-weight: 400;
	font-size: 14px;
	line-height: 22px;
	margin-bottom: 10px;
	max-width: 182px;
	flex: 1;

	@media (max-width: 576px) /* mobile */ {
		font-size: 11px;
		line-height: 141.9%;
		margin-bottom: 5px;
	}
}
.price {
	font-weight: 700;
}
.old {
	font-size: 20px;
	line-height: 24px;
	text-decoration-line: line-through;
	color: #c2ccca;
}
.new {
	font-size: 40px;
	line-height: 48px;
	color: var(--c-prim);
}
.btn {
	position: absolute;
	bottom: 0;
	right: 0;
	z-index: 10;
	width: 100px;
	height: 100px;
	clip-path: polygon(100% 0, 0 100%, 100% 100%);
	background-color: #fff;

	@media (max-width: 576px) /* mobile */ {
		width: 60px;
		height: 60px;
	}
}
.btn-icon-wrapper {
	display: flex;
	align-items: center;
	justify-content: center;
	position: relative;
	height: 100%;
}
.btn-icon {
	position: absolute;
	bottom: 0;
	right: 0;
	z-index: 1;
	width: 40px;
	height: 40px;

	@media (max-width: 576px) /* mobile */ {
		width: 30px;
		height: 30px;
	}
}
</style>
