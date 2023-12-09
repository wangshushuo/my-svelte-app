<script>
	import { onMount } from 'svelte';
	import { writable } from "svelte/store";

	/** @type { import("svelte/store").Writable<any[]> } */
	let tasks = writable( []);

	onMount(() => {
		tasks.set([
			{ id: 1, name: "Task 1" },
		])
	});
</script>

<ul>
	{#each $tasks as task}
		<li>{task.name}</li>
	{/each}
</ul>
<button on:click={() => tasks.update(t => [...t, { id: 2, name: "Task 2" }])}>Add</button>
