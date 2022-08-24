<script setup lang="ts">
import {
	TheHeader,
	TheFooter,
	HeroSect,
	StockSect,
	TheForm,
	TheSlider,
} from '@/components'
</script>

<template>
	<div class="wrapper">
		<the-header></the-header>
		<main class="main">
			<hero-sect></hero-sect>
			<the-slider></the-slider>
			<the-form></the-form>
			<stock-sect></stock-sect>
		</main>
		<the-footer></the-footer>
	</div>
</template>

<style scoped>
.wrapper {
	display: flex;
	flex-direction: column;
	min-height: 100vh;
	overflow-x: hidden;
}
.main {
	flex: 1 1 auto;
}
</style>
