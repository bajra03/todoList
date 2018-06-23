<template>
	<div>
		<p>Completed Tasks: {{ todos.filter(todo => {return todo.done === "true"}).length }}</p>
		<p>Pending Tasks: {{ todos.filter(todo => {return todo.done === "false"}).length }}</p>
		<!-- passing data on todo components to render on todoList components -->
		<todo v-for="todo in todos" v-bind:todo="todo" />
		<todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :todo.sync="todo"></todo>

		<div class="ui centered card" v-for="todo in todos">
			<div class="content">
				<div class="header">
					{{ todo.title }}
				</div>
				<div class="meta">
					{{ todo.project }}
				</div>
				<div class="extra content">
					<span class="right floated edit icon">
						<i class="edit icon"></i>
					</span>
				</div>
			</div>
			<div class="ui bottom attached green basic button" v-show="todo.done">
				Completed
			</div>
			<div class="ui bottom red basic button" v-show="!todo.done">
				Pending
			</div>
		</div>
	</div>
</template>

<!-- local script -->
<script>
	import todo from './todo';

	export default{
		props: ['todos'],
		components: {
			todo,
		},
		methods: {
			deleteTodo(todo){
				const todoIndex = this.todo.indexOf(todo);
				this.todo.splice(todoIndex, 1);
			},
			completeTodo(todo) {
		      const todoIndex = this.todos.indexOf(todo);
		      this.todos[todoIndex].done = true;
		    },
		},
	};
</script>

<!-- local style css -->
<style>
	
</style>