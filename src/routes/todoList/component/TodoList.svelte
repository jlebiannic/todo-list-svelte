<script lang="ts">
	import type { Todo } from "../model/Todo";
	import TodoItem from "./TodoItem.svelte";

	export let todos: Todo[];
</script>

<ul>
	{#each todos as todo (todo.id)}
		<li><TodoItem {todo} /></li>
	{/each}
</ul>
