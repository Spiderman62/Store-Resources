<template>
	<base-card>
		<base-button @click="setComponent('StoreResource')" :mode="storeResButtonMode">Store Resource</base-button>
		<base-button @click="setComponent('AddResource')" :mode="addResButtonMode">Add resource</base-button>
	</base-card>
	<KeepAlive>
		<component :is="currentComponent"></component>
	</KeepAlive>
</template>
<script>
import StoreResource from './StoreResource.vue';
import AddResource from './AddResource.vue';
export default {
	components: {
		StoreResource,
		AddResource
	},
	computed:{
		storeResButtonMode(){
			return this.currentComponent === 'StoreResource' ? null : 'flat'
		},
		addResButtonMode(){
			return this.currentComponent === 'AddResource' ? null : 'flat'
		}
	},	
	data() {
		return {
			storeResources: [
				{
					id: 'vue',
					title: 'Official-guide',
					description: 'The official Vue.js documentation',
					link: 'https://vuejs.org'
				},
				{
					id: 'google',
					title: 'Google',
					description: 'The official google documentation',
					link: 'https://www.bing.com/ck/a?!&&p=8e1c4b3e665a3304JmltdHM9MTcyNDM3MTIwMCZpZ3VpZD0yZGZkMTViMC1lMjg2LTYwYWYtMzI4Zi0wMWRiZTNlMDYxNzEmaW5zaWQ9NTE4OQ&ptn=3&ver=2&hsh=3&fclid=2dfd15b0-e286-60af-328f-01dbe3e06171&psq=google&u=a1aHR0cHM6Ly93d3cuZ29vZ2xlLmNvbS8&ntb=1'
				}
			],
			currentComponent: 'StoreResource'

		}
	},
	provide(){
		return{
			storeResources:this.storeResources,
			addResource:this.addResource,
			removeResource:this.removeResource
		}
	},
	methods: {
		setComponent(cpm) {
			this.currentComponent = cpm;
		},
		addResource(title,description,link){
			this.storeResources.unshift({
				id: new Date().toISOString(),
				title:title,
				description:description,
				link:link
			});
			this.currentComponent = 'StoreResource';

		},
		removeResource(id){
			const idx = this.storeResources.find(item=> item.id === id);
			this.storeResources.splice(idx,1);
		}
	}
}
</script>