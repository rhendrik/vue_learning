<template>
	<div>
		<form @submit="AddTodo">
			<input type="text" name="title" placeholder="Add Todo..." v-model="title">
			<input type="submit" name="submit" class="btn">
		</form>
	</div>
</template>

<script>
	export default{
		name: "AddTodo",
		data() {
			return {
				title: ''
			}
		},
		methods: {
			AddTodo(e){
				e.preventDefault();
				const newTodo = {
					title: this.title,
					completed: false
				}
				//send up to parent
				this.$emit('add-todo', newTodo);
				this.title = '';
			}
		}
	}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>