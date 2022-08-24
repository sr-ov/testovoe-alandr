<script setup lang="ts">
defineProps<{
	id: string
	name: string
	checked: boolean
}>()
</script>

<template>
	<label class="checkbox" :for="id">
		<input class="input" :checked="checked" type="radio" :name="name" :id="id" />
		<span class="pseudo"></span>
		<slot></slot>
	</label>
</template>

<style scoped>
.checkbox {
	display: inline-flex;
	align-items: center;
	gap: 7px;
	cursor: pointer;
}
.text {
	font-size: 14px;
	line-height: 17px;
	color: var(--c-prim);
}
.input:checked + .pseudo::after {
	opacity: 1;
}
.pseudo {
	width: 14px;
	height: 14px;
	border-radius: 50%;
	border: 1px solid var(--c-prim);
	background-color: #fff;
	position: relative;
}
.pseudo::after {
	content: '';
	position: absolute;
	top: 50%;
	left: 50%;
	z-index: 1;
	transform: translate(-50%, -50%);
	width: 8px;
	height: 8px;
	border-radius: 50%;
	background-color: var(--c-prim);
	opacity: 0;
	transition: opacity 0.2s;
}
</style>
