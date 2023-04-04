<script lang="ts">
	import { Todo } from "../model/Todo";
	import type { TodoEvent } from "./TodoItem.svelte";
	import TodoList from "./TodoList.svelte";

	let libelleTodo = "";
	let todos: Todo[] = [];
	function ajouteTodo() {
		todos = [...todos, new Todo(todos.length, libelleTodo)];
	}

	// function onCocheTodo(event: CustomEvent<TodoEvent>) {
	// 	//alert("onCocheTodo " + event.detail.todoId);
	// 	const index = getIndexTodo(event.detail.todoId);
	// 	console.log("event", index);
	// 	todos[index].coche = !todos[index].coche;
	// 	todos = [...todos];
	// 	console.log(todos);
	// }

	function onSupprimeTodo(event: CustomEvent<TodoEvent>) {
		//alert("onSupprimeTodo " + event.detail.todoId);
		supprimeTodo(event.detail.todoId);
	}

	function getIndexTodo(todoId: number) {
		return todos.findIndex((todo) => todo.id === todoId);
	}

	function supprimeTodo(todoId: number) {
		const index = getIndexTodo(todoId);
		todos.splice(index, 1);
		todos = [...todos];
	}
</script>

<input bind:value={libelleTodo} /><button on:click={ajouteTodo}>Ajouter</button>
<TodoList {todos} on:onSupprimeTodo={onSupprimeTodo} />
