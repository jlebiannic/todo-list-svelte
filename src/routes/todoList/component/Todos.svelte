<script lang="ts">
	import { Todo } from "../model/Todo";
	import TodoList from "./TodoList.svelte";

	let libelleTodo = "";
	let todos: Todo[] = [];
	function ajouteTodo() {
		todos = [...todos, new Todo(todos.length, libelleTodo)];
	}
</script>

<input bind:value={libelleTodo} /><button on:click={ajouteTodo}>Ajouter</button>
<TodoList {todos} />
