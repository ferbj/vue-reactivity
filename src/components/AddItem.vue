<template>
	<div class="m-2">
		<form @submit.prevent="addItem" class="form-horizontal">
			<div class="form-group col-4">
				<input type="text" v-model="title" name="title" class="form-control">
			</div>
			<div class="form-group col-4">
				<input type="submit" value="Submit" class="btn btn-success">
			</div>
		</form>
	</div>
</template>
<script>
	import {v4 as uuidv4 } from 'uuid';
	export default{
		name: "AddItem",
		data(){
			return {
				title:''
			}
		},

		methods:{
			addItem(){
				let bool = Math.random() >= 0.5;
				const newItem = {
					id : uuidv4(),
					title:this.title, 
					completed: bool
				}
				this.title = '';
				//thats emit a event and then capture on App.vue
				this.$emit('add-item',newItem)
			}
		}
	}
</script>