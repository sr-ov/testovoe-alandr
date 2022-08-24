<script setup lang="ts"></script>

<template>
	<div class="stock">
		<div class="container">
			<div class="content">
				<div class="top">
					У на осталось еще:
					<a class="top__link" href="#">25&nbsp;ёжиков</a>
				</div>
				<div class="btm">
					Торопитесь! Акция <br />
					действует до 26. 02. 2023
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped lang="scss">
.stock {
	padding-top: 30px;
	padding-bottom: 60px;

	@media (max-width: 480px) /* mobile_sm */ {
		padding-bottom: 50px;
	}
}
.content {
	text-align: center;
	color: var(--c-sec);

	@media (max-width: 480px) /* mobile_sm */ {
		text-align: initial;
	}
}
.top {
	margin-bottom: 25px;
	font-weight: 700;
	font-size: 24px;
	line-height: 29px;

	&__link {
		text-decoration: underline;
		font-weight: inherit;
	}
}
.btm {
	font-family: var(--ff-sec);
	font-weight: 400;
	font-size: 14px;
	line-height: 22px;
	font-feature-settings: 'pnum' on, 'lnum' on;
}
</style>
