<script lang="ts">
	import TodoList from "./component/TodoList.svelte";
	import { Todo } from "./model/Todo";

	let libelleTodo = "";
	let todos: Todo[] = [];
	function ajouteTodo() {
		todos = [...todos, new Todo(todos.length, libelleTodo)];
	}
</script>

<input bind:value={libelleTodo} /><button on:click={ajouteTodo}>Ajouter</button>
<TodoList {todos} />
