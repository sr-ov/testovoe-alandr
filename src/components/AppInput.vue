<script setup lang="ts">
import { useMediaQuery } from '@vueuse/core'

defineProps<{ isTextarea?: boolean }>()

const isMoreThanMobile = useMediaQuery('(min-width: 576px)')
</script>

<template>
	<textarea class="input" v-if="isTextarea && isMoreThanMobile" rows="3"></textarea>
	<input class="input" v-else type="text" />
</template>

<style scoped lang="scss">
.input {
	background-color: #f8f8f8;
	border-radius: 8px;
	padding: 20px 27px;
	display: block;
	width: 100%;
	font-family: var(--ff-sec);
	transition: box-shadow 0.2s;

	&::placeholder {
		color: var(--c-prim);
	}

	&:focus {
		box-shadow: 0 0 0 2px var(--c-prim);
	}
}
</style>
