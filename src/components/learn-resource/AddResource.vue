<template>
	<base-dialog v-if="valueIsInvalid" title="Invalid Input" @close="confirmError">
	<template #default>
		<p>Unfortunately, at least one input value is invalid.</p>
		<p>Please check all inputs and make sure you enter at least</p>
	</template>
	<template #actions>
		<base-button @click="confirmError">Close</base-button>
	</template>
	</base-dialog>
	<base-card>
		<form @submit.prevent="submitData" action="">
			<div class="input-box">
				<label for="title">Title</label>
				<input name="title" id="title" type="text" ref="title">
			</div>
			<div class="input-box">
				<label for="description">Description</label>
				<textarea name="description" id="description" rows="3" ref="description"></textarea>
			</div>
			<div class="input-box">
				<label for="link">Link</label>
				<input name="link" id="link" type="url" ref="link">
			</div>
			<base-button type="submit">Add Resource</base-button>
		</form>
	</base-card>
</template>
<script>
export default {
	inject: ['addResource'],
	data() {
		return {
			valueIsInvalid: false
		}
	},
	methods: {
		submitData() {
			const title = this.$refs.title.value;
			const description = this.$refs.description.value;
			const link = this.$refs.link.value;
			if (title.trim() === '' || description.trim() === '' || link.trim() === '') {
				this.valueIsInvalid = true;
				return;
			}
			this.addResource(title, description, link);
		},
		confirmError(){
			this.valueIsInvalid = false;
		}
	}
}
</script>
<style scoped>
label {
	font-weight: bold;
	display: block;
	margin-block: .5rem;
	font-size: 1.8rem;
}

.input-box {
	margin: 1rem 0;
}

input {
	padding: 0 15px 0 5px;
	height: 40px;
}

textarea {
	padding: 4px;
}

input,
textarea {
	display: block;
	width: 100%;
	font-family: inherit;
	border: 1px solid #ccc;
	font-size: 1.8rem;
}

input:focus,
textarea:focus {
	outline: none;
	border-color: #3a0061;
	background-color: #f7ebff;
}
p{
	font-size: 1.8rem;
}
</style>