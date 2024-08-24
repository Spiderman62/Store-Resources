<template>
	<base-card>
	<li>
		<header>
			<h1>{{ title }}</h1>
			<base-button  @click="deleteResource(id)">Delete</base-button>
		</header>
		<section>
			<p>{{ description }}</p>
		</section>
		<menu>
			<a :href="link">View resource</a>
		</menu>
	</li>
	</base-card>
</template>
<script>
export default {
	props: ['id', 'title', 'description', 'link'],
	inject:['deleteResource'],
}
</script>
<style scoped>
li {
	list-style: none;
}

li header {
	display: flex;
	justify-content: space-between;
	align-items: center;
}

li h1 {
	font-size: 2.5rem;
	font-weight: 500;
}

li section p {
	font-size: 1.8rem;
	margin: 8px 0 12px;
}

li a {
	font-size: 1.6rem;
	text-decoration: none;
	color: rgb(66, 211, 147);
}
</style>