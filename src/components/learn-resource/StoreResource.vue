<template>
	<ul>
		<LearnResource v-for="item in storeResources" :key="item.id" :id="item.id" :title="item.title" :description="item.description"
			:link="item.link"></LearnResource>
	</ul>
</template>
<script>
import LearnResource from './LearnResource.vue';
export default {
	components:{
		LearnResource
	},
	inject:['storeResources']
}
</script>
<style scoped>
ul{
	max-width: 800px;
	margin: auto;
	list-style: none;
}
</style>