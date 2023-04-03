<script lang="ts">
	import { Todo } from "../model/Todo";
	import type { TodoEvent } from "./TodoItem.svelte";
	import TodoList from "./TodoList.svelte";

	let libelleTodo = "";
	let todos: Todo[] = [];
	function ajouteTodo() {
		todos = [...todos, new Todo(todos.length, libelleTodo)];
	}

	function onCocheTodo(event: CustomEvent<TodoEvent>) {
		console.log("event", event);
		alert("onCocheTodo " + event.detail.todoId);
	}

	function onSupprimeTodo(event: CustomEvent<TodoEvent>) {
		alert("onSupprimeTodo " + event.detail.todoId);
	}
</script>

<input bind:value={libelleTodo} /><button on:click={ajouteTodo}>Ajouter</button>
<TodoList {todos} on:onCocheTodo={onCocheTodo} on:onSupprimeTodo={onSupprimeTodo} />
