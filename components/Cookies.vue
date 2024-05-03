<template>
	<div class="cookie-banner" v-if="showBanner">
		<div class="cookie-banner-content">
			<p>
				This website uses cookies to ensure you get the best experience. By continuing to use this site, you consent to the use of cookies.
			</p>
			<button @click="acceptCookies">Accept</button>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Cookies',
	data() {
		return {
			showBanner: true
		};
	},
	beforeMount() {
		const cookies = document.cookie.split('; ');
    const cookieAcceptance = cookies.find(row => row.startsWith('cookieAcceptance'));

    if (cookieAcceptance) {
      this.showBanner = false;
    }
	},
	methods: {
		acceptCookies() {
      const date = new Date();
      date.setFullYear(date.getFullYear() + 1);
      document.cookie = `cookieAcceptance=${date.getTime()}; expires=${date.toUTCString()}; path=/`;

			this.showBanner = false;
		}
	}
};
</script>

<style scoped>
.cookie-banner { 
	width: 100%;
	background-color: var(--md-sys-color-primary-container);
	padding: 10px;
	position: fixed;
	bottom: 0;
	left: 0;
}

.cookie-banner-content {
	display: flex;
	justify-content: space-between;
	align-items: center;
	flex-direction: column;
}

p {
	margin: 0;
	margin-bottom: 10px;
	color: var(--md-sys-color-on-primary-container);
}

button {
	background-color: var(--md-sys-color-primary);
	border: none;
	border-radius: 10px;
	color: var(--md-sys-color-on-primary);
	padding: 5px 8px;
	text-align: center;
	text-decoration: none;
	display: inline-block;
	font-size: 16px;
	cursor: pointer;
}
</style>