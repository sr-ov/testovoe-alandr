<script setup lang="ts">
import { AppLogo, AppNav, AppPhone } from '.'
import IconFacebook from './icons/IconFacebook.vue'
import IconInstagram from './icons/IconInstagram.vue'
import IconTwitter from './icons/IconTwitter.vue'

const social = [IconInstagram, IconFacebook, IconTwitter]

const items = [
	{ text: 'Каталог' },
	{ text: 'о\xa0нас' },
	{ text: 'контакты' },
	{ text: 'галерея' },
]
</script>

<template>
	<footer class="footer">
		<div class="container">
			<div class="content">
				<div class="wrapper">
					<div class="row">
						<div class="logo">
							<app-logo color-white in-footer></app-logo>
						</div>
						<div class="nav">
							<app-nav text-white col-mobile :nav-items="items"></app-nav>
						</div>
						<div class="social">
							<ul class="social-list">
								<li class="social-item" v-for="el in social">
									<a class="social-link" href="#">
										<component :is="el"></component>
									</a>
								</li>
							</ul>
						</div>
						<div class="phone">
							<app-phone text-white></app-phone>
						</div>
					</div>
					<div class="copyright">
						Все права защищены. <br />
						Указанная стоимость товаров и условия их приобретения действительны на
						текущую дату.
					</div>
				</div>
			</div>
		</div>
	</footer>
</template>

<style scoped>
.footer {
	--py: 36px;

	color: #fff;
	background-color: var(--c-prim);
	padding: var(--py) 0;
}
.content {
	display: flex;
	align-items: center;
}
.wrapper {
	flex: 1;
}
.row {
	display: flex;
	align-items: center;
	margin-bottom: 24px;
}
.logo {
	flex: 1;
	margin-right: 20px;
}
.nav {
	margin-right: 99px;
}
.social {
	margin-right: 70px;
}
.social-list {
	display: flex;
	align-items: center;
}
.social-link {
	display: flex;
	align-items: center;
	justify-content: center;
}
.copyright {
}

@media (max-width: 991px) {
	.nav {
		margin-right: 20px;
	}
	.social {
		margin-right: 20px;
	}
}

@media (max-width: 768px) {
	.row {
		display: block;
		align-items: center;
	}
	.row > * {
		margin-bottom: 30px;
	}
}

@media (max-width: 480px) {
	.row {
		display: block;
		align-items: center;
		position: relative;
	}
	.row > * {
		margin-bottom: 30px;
	}
	.social {
		position: absolute;
		top: 0;
		right: 0;
		z-index: 1;
	}
	.social-list {
		flex-direction: column;
		gap: 12px;
	}
}
</style>
