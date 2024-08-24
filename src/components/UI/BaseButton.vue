<template>
	<button :type="type" :class="isClass">
		<slot></slot>
	</button>
</template>
<script>
export default {
	props:['type','isClass']
}
</script>
<style scoped>
	button{
		padding: 12px 24px;
		font-size: 1.8rem;
		border: none;
		background-color: rgba(37, 177, 58, 0.345);
		cursor: pointer;
		transition: .2s ease-in-out;
		border-radius: 2px;
	}
	button:hover{
		background-color: rgb(69,211,148);
		color:white;
	}
	.flat{
		background: transparent;
		color: black;
		transition: .2s ease-in-out;
	}
	.flat:hover{
		background-color: rgba(37, 177, 58, 0.345);
		color: black;
	}
</style>