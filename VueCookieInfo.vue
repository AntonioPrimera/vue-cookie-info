<template>
	<div v-if="show" class="vue-cookie-info" ref="root">
		<p v-text="text" class="vci-text"></p>
		<button class="vci-button" v-text="button" @click="understood"></button>
	</div>
</template>

<script>
import CookieManager from "js-cookie-manager";

export default {
	props: {
		text: String,
		button: {
			type: String,
			'default': 'OK'
		},
		cookieName: {
			type: String,
			'default': 'cookie-policy-accepted'
		}
	},
	
	data() {
		return {
			cookieManager: null,
			show: true,
		}
	},
	
	methods: {
		understood() {
			this.cookieManager.set(this.cookieName, '1', 365);
			this.show = false;
		}
	},
	
	mounted() {
		//check if we should display the info box
		this.cookieManager = new CookieManager();
		this.show = ! this.cookieManager.has(this.cookieName);
		
		//if any class was applied externally to the current component, remove the default class
		if (this.$refs.root.classList.length > 1) this.$refs.root.classList.remove('vue-cookie-info');
	},
}
</script>

<style lang="scss" scoped>
	
	.vue-cookie-info{
		font-size: 0.75rem;
		position: fixed;
		padding: .5rem;
		background: white;
		border: 2px solid #420042;
		box-shadow: 0 5px 5px #420042;
		display: flex;
		flex-flow: column;
		align-items: center;
		text-align: center;
		bottom: .25rem;
		left: .25rem;
		right: .25rem;
		
		.vci-text{
			margin-bottom: .5rem;
		}
		
		.vci-button{
			padding: .5rem 1rem;
			background: #420042;
			color: white;
			text-transform: uppercase;
		}
	}
	
	@media (min-width: 1024px) {
		.vue-cookie-info{
			padding: 1.5rem;
			flex-flow: row;
			text-align: left;
			
			.vci-text{
				margin-bottom: 0;
				margin-right: 3rem;
			}
		}
	}
</style>
