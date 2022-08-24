<script setup lang="ts">
import { AppButton, AppCheckbox, AppCheckboxButton, AppInput } from '.'

const variable = () => {}

const leftCheckboxes = [
	'хочу ёжика для себя',
	'хочу ёжика для детей',
	'хочу ёжика для разведения',
]
const rightCheckboxes = [
	'Мне нужен 1-2 ёжика',
	'Мне нужны 3-4 ёжика',
	'Мне нужны 3 и более ёжиков',
	'Пока присматриваюсь',
]
const inputs = ['Ваше имя', 'Ваш телефон', 'Ваш e-mail']
</script>

<template>
	<div class="form-sect">
		<div class="container-sm container-sm--px0">
			<form class="form" action="/" @submit.prevent>
				<h2 class="form-title">
					Заполните заявку и мы забронируем для Вас нового друга
				</h2>

				<div class="top">
					<ul class="top-left">
						<li v-for="(text, i) in leftCheckboxes">
							<app-checkbox-button
								:checked="i === 0"
								name="leftCheckboxes"
								:id="text"
							>
								{{ text }}
							</app-checkbox-button>
						</li>
					</ul>
					<ul class="top-right">
						<li v-for="(text, i) in rightCheckboxes">
							<app-checkbox :checked="i === 0" name="rightCheckboxes" :id="text">
								{{ text }}
							</app-checkbox>
						</li>
					</ul>
				</div>

				<div class="btm">
					<ul class="btm-top">
						<li v-for="placeholder in inputs">
							<app-input :placeholder="placeholder"></app-input>
						</li>
					</ul>
					<div class="btm-btm">
						<app-input is-textarea placeholder="Комментарий к заявке"></app-input>
					</div>
				</div>
				<div class="submit-btn-wrapper">
					<app-button class="submit-btn">Купить ёжика</app-button>
				</div>
			</form>
		</div>
	</div>
</template>

<style scoped lang="scss">
.form-sect {
	padding-top: 42px;
	padding-bottom: 65px;
}
.form {
	padding: 30px 50px 80px;
	background-color: #eaeeef;
	border-radius: 30px;
	position: relative;

	@media (max-width: 576px) /* mobile */ {
		border-radius: initial;
		padding: 40px 15px;
	}
}
.form-title {
	font-weight: 700;
	font-size: 45px;
	line-height: 54px;
	color: var(--c-sec);
	margin-bottom: 30px;

	@media (max-width: 576px) /* mobile */ {
		font-size: 24px;
		line-height: 29px;
		margin-bottom: 25px;
	}
}
.top {
	display: flex;
	align-items: center;
	gap: 77px;
	margin-bottom: 43px;

	@media (max-width: 1220px) {
		flex-direction: column;
		gap: 30px;
	}
	@media (max-width: 768px) /* tablet_sm */ {
		align-items: flex-start;
	}
}
.top-left {
	display: grid;
	grid-template-columns: repeat(3, auto);
	gap: 14px;

	@media (max-width: 768px) /* tablet_sm */ {
		grid-template-columns: 1fr;
	}
}
.top-right {
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	gap: 10px 50px;

	@media (max-width: 480px) /* mobile_sm */ {
		grid-template-columns: 1fr;
	}
}

.btm-top {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	gap: 20px;
	margin-bottom: 20px;

	@media (max-width: 768px) /* tablet_sm */ {
		grid-template-columns: 1fr;
	}
}

.submit-btn-wrapper {
	position: absolute;
	bottom: 0;
	left: 50%;
	z-index: 1;
	transform: translate(-50%, 50%);

	@media (max-width: 576px) /* mobile */ {
		position: initial;
		transform: initial;
		margin-top: 25px;
	}
}
.submit-btn {
	min-width: 328px;
	min-height: 70px;

	@media (max-width: 576px) /* mobile */ {
		min-width: 100%;
	}
}
</style>
