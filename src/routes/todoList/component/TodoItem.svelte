<script context="module" lang="ts">
	export interface TodoEvent {
		todoId: number;
	}
</script>

<script lang="ts">
	import { createEventDispatcher } from "svelte";
	import type { Todo } from "../model/Todo";

	export let todo: Todo;
	const dispatch = createEventDispatcher();

	function onCocheTodo(todoId: number) {
		dispatch("onCocheTodo", { todoId });
	}

	function onSupprimeTodo(todoId: number) {
		dispatch("onSupprimeTodo", { todoId });
	}
</script>

<input
	type="checkbox"
	on:click={(e) => {
		e.preventDefault();
		onCocheTodo(todo.id);
	}}
	checked={todo.coche}
/>
<span>{todo.libelle}</span>
<!-- Icone poubelle -->
<span
	on:click={() => onSupprimeTodo(todo.id)}
	on:keydown={() => onSupprimeTodo(todo.id)}
	style="cursor: pointer">&#128465;</span
>
