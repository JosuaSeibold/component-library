<template>
	<div class="footer">
		<div class="footer-links">
			<a href="/imprint" class="footer-link">Imprint</a>
			<a href="/datenschutz" class="footer-link">Data Protection</a>
			<p @click="openCookieSettings" class="footer-link">Cookies</p>
		</div>
		<p>&copy; {{ currentYear }} Spielekiste & Josua Seibold. All rights reserved.</p>
	</div>
</template>

<script>
export default {
	name: 'Footer',
	data() {
		return {
			currentYear: new Date().getFullYear(),
		}
	},
	methods: {
		openCookieSettings() {
			this.$emit('openCookieSettings');
		}
	}
}
</script>

<style scoped>
.footer {
	background-color: var(--md-sys-color-background);
	padding: 20px;
	text-align: center;
	color: var(--md-sys-color-on-background);
}

p, a {
	color: var(--md-sys-color-on-surface);
	font-size: 20px;
	margin: 0;
}

.footer-links {
	margin-bottom: 10px;
	display: flex;
	justify-content: center;
	gap: 30px;
}

.footer-link {
	color: var(--md-sys-color-on-background);
	text-decoration: none;
	cursor: pointer;
}
</style>