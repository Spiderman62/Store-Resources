<template>
	<base-card>
		<base-button @click="setComponent('store-resource')" :isClass="storeResource">Store resource</base-button>
		<base-button @click="setComponent('add-resource')" :isClass="addResource">Add resource</base-button>
	</base-card>
	<keep-alive>
		<component :is="currentComponent"></component>
	</keep-alive>
</template>
<script>
import StoreResource from './StoreResource.vue';
import AddResource from './AddResource.vue';
export default {
	components:{
		AddResource,
		StoreResource
	},
	computed:{
		storeResource(){
			return this.currentComponent === 'store-resource' ? '' : 'flat';
		},
		addResource(){
			return this.currentComponent === 'add-resource' ? '' : 'flat';
		}
	},
	data(){
		return{
			storeResources:[
				{
					id:'Vue',
					title:'Vue',
					description:'The offcial framework using by VueJs!',
					link:'https://vuejs.org'
				},
				{
					id:'React',
					title:'React',
					description:'The offcial framework using by ReactJs!',
					link:'https://react.dev/'
				},
			],
			currentComponent:'store-resource'
		}
	},
	provide(){
		return{
			storeResources:this.storeResources,
			addStoreResource:this.addStoreResource,
			deleteResource:this.deleteResource
		}
	},
	methods:{
		setComponent(cpm){
			this.currentComponent = cpm;
		},
		addStoreResource(title,description,link){
			this.storeResources.unshift({
				id:new Date().toISOString(),
				title:title,
				description:description,
				link:link
			});
			this.currentComponent = 'store-resource';
		},
		deleteResource(id){
			const idx = this.storeResources.findIndex(item => item.id === id);
			this.storeResources.splice(idx,1);
		}
	}
}
</script>