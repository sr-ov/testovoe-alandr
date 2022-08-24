<script setup lang="ts">
import IconLogo from './icons/IconLogo.vue'

defineProps<{ colorWhite?: boolean; inFooter?: boolean }>()
</script>

<template>
	<div :class="[$style.logo, { [$style.in_footer]: inFooter }]">
		<icon-logo
			:class="$style.logo_icon"
			width="120"
			height="56"
			:color-white="colorWhite"
		></icon-logo>
	</div>
</template>

<style module>
.logo {
	--logo-h: 56px;
	--logo-w: 120px;
}
.logo_icon {
	height: var(--logo-h);
	width: var(--logo-w);
}

@media (max-width: 576px) {
	.logo:not(.in_footer) {
		--logo-h: 26px;
		--logo-w: 56px;
	}
}
</style>
