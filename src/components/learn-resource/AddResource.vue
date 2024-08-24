<template>
	<base-popup v-if="isValueInvalid" title="Invalid value" @close="confirmClose">
		<p>Unfortunately, there are some input value is incorrect!</p>
		<p>Please, can not be blank and fill input must correct </p>
	</base-popup>
	<base-card>
		<form action="" @submit.prevent="submitData">
			<div class="input-box">
				<label for="title">Title</label>
				<input type="text" id="title" name="title" ref="title">
			</div>
			<div class="input-box">
				<label for="description">Description</label>
				<textarea name="description" id="description" cols="30" rows="3" ref="description"></textarea>
			</div>
			<div class="input-box">
				<label for="url">Link</label>
				<input type="url" id="url" name="url" ref="link">
			</div>
			<base-button type="submit">Add resource</base-button>
		</form>
	</base-card>
</template>
<script>
export default {
	inject: ['addStoreResource'],
	data() {
		return {
			isValueInvalid: false
		}
	},
	methods: {
		submitData() {
			const title = this.$refs.title.value.trim();
			const description = this.$refs.description.value.trim();
			const link = this.$refs.link.value.trim();
			if (title === '' || description === '' || link === '') {
				this.isValueInvalid = true;
				return;
			}
			this.addStoreResource(title, description, link);
		},
		confirmClose(){
			this.isValueInvalid = false;
		}
	},
}
</script>
<style>
label {
	display: block;
	font-size: 1.8rem;
	margin-bottom: 4px;
}

.input-box {
	margin: 0 0 18px;
}

input {
	width: 100%;
	height: 40px;
	outline: none;
	border: 1px solid black;
	border-radius: 2px;
	padding: 0 15px 0 5px;
	font-size: 1.8rem;
}

textarea {
	width: 100%;
	height: 80px;
	padding: 4px;
	font-size: 1.8rem;
	outline: none;
}

input:focus,
textarea:focus {
	background-color: rgba(66, 211, 148, 0.142);
}
p{
	font-size: 1.8rem;
}
</style>