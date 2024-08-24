<template>
	<ul>
		<LearnResource v-for="resource in storeResources" :key="resource.id" :id="resource.id" :title="resource.title"
			:description="resource.description" :link="resource.link"></LearnResource>
	</ul>
	
</template>
<script>
import LearnResource from './LearnResource.vue';
export default {
	components: {
		LearnResource
	},
	inject: ['storeResources']
}
</script>