<script context="module" lang="ts">
	export interface onCocheTodoEvent {
		onCocheTodo: number;
	}

	export interface onSupprimeTodoEvent {
		onSupprimeTodo: number;
	}
</script>

<script lang="ts">
	import { createEventDispatcher } from "svelte";
	import type { Todo } from "../model/Todo";

	export let todo: Todo;
	const dispatch1 = createEventDispatcher<onCocheTodoEvent>();
	const dispatch2 = createEventDispatcher<onSupprimeTodoEvent>();

	function onCocheTodo(todoId: number) {
		dispatch1("onCocheTodo", todoId);
	}

	function onSupprimeTodo(todoId: number) {
		dispatch2("onSupprimeTodo", todoId);
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
