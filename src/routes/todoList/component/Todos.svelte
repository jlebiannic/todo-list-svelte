<script lang="ts">
	import { Todo } from "../model/Todo";
	import type { onCocheTodoEvent, onSupprimeTodoEvent } from "./TodoItem.svelte";
	import TodoList from "./TodoList.svelte";

	let libelleTodo = "";
	let todos: Todo[] = [];
	function ajouteTodo() {
		todos = [...todos, new Todo(todos.length, libelleTodo)];
	}

	function onCocheTodo(event: CustomEvent<onCocheTodoEvent>) {
		alert("onCocheTodo " + event.detail.onCocheTodo);
	}

	function onSupprimeTodo(event: CustomEvent<onSupprimeTodoEvent>) {
		alert("onSupprimeTodo" + event.detail.onSupprimeTodo);
	}
</script>

<input bind:value={libelleTodo} /><button on:click={ajouteTodo}>Ajouter</button>
<TodoList {todos} on:onCocheTodo={onCocheTodo} on:onCocheTodo={onSupprimeTodo} />
