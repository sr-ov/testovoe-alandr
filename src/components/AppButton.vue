<script setup lang="ts"></script>

<template>
	<button :class="$style.btn">
		<span :class="$style.text">
			<slot></slot>
		</span>
	</button>
</template>

<style module lang="scss">
.btn {
	background-color: var(--c-prim);
	display: flex;
	align-items: center;
	justify-content: center;
	padding: 10px 15px;
	overflow: hidden;
	position: relative;
	box-shadow: var(--bx-sh-prim);
	border-radius: var(--bd-prim);
	border: none;
	transition: transform 0.1s;

	&:active {
		transform: scale(0.95);
	}
}
.btn:hover::after {
	opacity: 1;
}
.btn:hover .text {
	color: var(--c-sec);
}
.btn::after {
	transition: opacity 0.3s;
	content: '';
	opacity: 0;
	position: absolute;
	top: 0;
	left: 0;
	bottom: 0;
	right: 0;
	z-index: 1;
	background-image: linear-gradient(90.14deg, #b0d3ce -2.41%, #ffedce 99.79%);
}
.text {
	transition: color 0.3s;
	color: #fff;
	font-family: var(--ff-sec);
	font-weight: 700;
	font-size: 14px;
	line-height: 16px;
	position: relative;
	z-index: 10;
}

@media (max-width: 576px) {
	.btn {
		width: auto;
		height: auto;
	}
}
</style>
