<template>
	<li>
		<base-card>
			<header>
				<h3>{{ title }}</h3>
				<base-button mode="flat" @click="removeResource(id)">Delete</base-button>
			</header>
			<p>{{ description }}</p>
			<nav>
				<a :href="link">View Resource</a>
			</nav>
		</base-card>
	</li>
</template>
<script>
import BaseCard from '../UI/BaseCard.vue'
export default {
  components: { BaseCard },
	props:['id','title','description','link'],
	inject:['removeResource']
}
</script>
<style scoped>
li{
	margin: 10px 0;
}
header{
	display: flex;
	justify-content: space-between;
	align-items: center;
}
p{
	margin: .5rem 0;
	font-size: 1.8rem;
}
h3{
	font-size: 2.5rem;
	margin: .5rem 0;
}
a{
	text-decoration: none;
	color: #ce5c00;
	font-size: 1.6rem;
}
a:hover,
a:active{
	color: #c89300;
}
button{
	font-size: 1.8rem;

}
</style>