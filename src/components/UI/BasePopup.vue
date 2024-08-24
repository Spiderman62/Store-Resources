<template>
	<teleport to="#app">
		<section @click="$emit('close')">
			<div class="wrapper" @click.stop>
				<header>
					<h1>{{ title }}</h1>
				</header>
				<div class="describe">
					<slot></slot>
				</div>
				<menu>
					<base-button @click="$emit('close')">Okay</base-button>
				</menu>
			</div>
		</section>
	</teleport>
</template>
<script>
export default {
	props:['title'],
	emits:['close']
}
</script>
<style scoped>
section{
	position: fixed;
	inset: 0;
	display: flex;
	justify-content: center;
	align-items: center;
	z-index: 100;
	backdrop-filter: blur(5px);
}
header{
	height: 50px;
	background-color: rgb(180,228,187);
}
h1{
	line-height: 50px;
	font-size: 2.0rem;
	margin-left: 10px;
}
.wrapper{
	width: 600px;
	border-radius: 8px;
	background-color: white;
	box-shadow: 0 0 20px 2px rgb(227, 226, 226) ;
	overflow: hidden;
}
.describe{
	padding: 20px;
}
menu{
	display: flex;
	justify-content: flex-end;
	border-top: 1px solid rgb(224, 221, 221);
	padding: 10px;
}
</style>