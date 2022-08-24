<script setup lang="ts">
import IconRightArrow from './icons/IconRightArrow.vue'

interface SubItem {
	text: string
}

interface NavItem {
	text: string
	sub?: SubItem[]
}

interface Props {
	textWhite?: boolean
	colMobile?: boolean
	navItems: NavItem[]
}

defineProps<Props>()
</script>

<template>
	<nav>
		<ul class="nav-list" :class="{ 'col-mobile': colMobile }">
			<li class="nav-item" v-for="item in navItems">
				<div class="subnav-wrapper" v-if="item.sub">
					<div class="subnav-title-wrapper">
						<icon-right-arrow class="subnav-title-icon"></icon-right-arrow>
						<div class="subnav-title" :class="{ 'text-white': textWhite }">
							{{ item.text }}
						</div>
					</div>
					<div class="subnav">
						<ul class="subnav-list">
							<li class="subnav-item" v-for="el in item.sub">
								<a class="nav-link" :class="{ 'text-white': textWhite }" href="#">
									{{ el.text }}
								</a>
							</li>
						</ul>
					</div>
				</div>

				<a class="nav-link" :class="{ 'text-white': textWhite }" v-else href="#">
					{{ item.text }}
				</a>
			</li>
		</ul>
	</nav>
</template>

<style scoped>
.nav-list {
	display: flex;
	align-items: center;
	flex-wrap: wrap;
	gap: 10px 80px;
}
.nav-item {
}
.nav-link,
.subnav-title {
	padding: 8px 0;
	font-weight: 700;
	font-size: 16px;
	line-height: 19px;
	text-transform: uppercase;
	color: var(--c-sec);
	position: relative;
}
.nav-link::after,
.subnav-title::after {
	content: '';
	position: absolute;
	left: 0;
	bottom: 5px;
	z-index: 1;
	width: 100%;
	height: 1px;
	background-color: var(--c-sec);
	transition: opacity 0.3s;
	opacity: 0;
}
.nav-link:hover::after,
.subnav-title:hover::after {
	opacity: 1;
}
.subnav-title-wrapper {
	display: flex;
	align-items: center;
	gap: 7px;
}
.subnav-title-icon {
	transition: transform 0.3s;
}
.subnav-wrapper {
	position: relative;
}
.subnav-wrapper:hover .subnav-title::after {
	opacity: 1;
}
.subnav-wrapper:hover .subnav {
	opacity: 1;
	visibility: visible;
}
.subnav-wrapper:hover .subnav-title-icon {
	transform: rotate(90deg);
}
.subnav {
	position: absolute;
	top: 100%;
	left: 0;
	z-index: 1;
	padding-top: 16px;
	transition: opacity 0.3s, visibility 0.3s;
	opacity: 0;
	visibility: hidden;
}
.subnav-list {
	background-color: #fffefe;
	box-shadow: 4px 4px 20px #c2ccca;
	border-radius: 8px;
	padding: 20px 24px;
	min-width: 170px;
}
.subnav-item + .subnav-item {
	margin-top: 20px;
}

.text-white {
	color: #fff;
}
.text-white.nav-link::after,
.text-white.subnav-title::after {
	background-color: #fff;
}

@media (max-width: 1300px) {
	.nav-list {
		gap: 10px 30px;
	}
}

@media (max-width: 576px) {
	.nav-list.col-mobile {
		flex-direction: column;
		align-items: start;
		row-gap: 30px;
	}
}
</style>
