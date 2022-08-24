<script setup lang="ts">
defineProps<{
	id: string
	name: string
	checked: boolean
}>()
</script>

<template>
	<label :class="$style.checkbox" :for="id">
		<input
			:class="$style.input"
			:checked="checked"
			type="radio"
			:name="name"
			:id="id"
		/>
		<span :class="$style.pseudo"></span>
		<span :class="$style.text">
			<slot></slot>
		</span>
	</label>
</template>

<style module lang="scss">
.checkbox {
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: #fff;
	cursor: pointer;
	box-shadow: inset 0 0 0 2px var(--c-prim);
	border-radius: 61px;
	transition: background-color 0.2s;
	overflow: hidden;
	padding: 16px 22px;
}
.text {
	font-size: 14px;
	line-height: 17px;
	color: var(--c-prim);
	transition: color 0.2s;
	position: relative;
	z-index: 1111;
	transition: color 0.2s;
}

@media (any-hover: hover) {
	.checkbox:hover {
		background-color: var(--c-prim);
	}
	.checkbox:hover .text {
		color: #fff;
	}
}

.input:checked ~ .pseudo {
	opacity: 1;
}

.input:checked ~ .text {
	color: #fff;
}
.input {
	position: absolute;
	z-index: -111;
	appearance: none;
}
.pseudo {
	position: absolute;
	top: 0;
	left: 0;
	z-index: 1;
	background-color: var(--c-prim);
	width: 100%;
	height: 100%;
	opacity: 0;
	transition: opacity 0.2s;
}
</style>
