<!-- 3. Render the list here -->
<script>
    import TodoListItem from "./TodoListItem.svelte";
    import { createEventDispatcher } from 'svelte';
    import {Row} from "sveltestrap";

    export let todos

    const dispatch = createEventDispatcher();
    const updateCheck = (changedTodo) => {
        const todo = changedTodo.detail.todo
        const index = changedTodo.detail.index
        dispatch('update',{
            todo: todo,
            index: index
        });
    }
    const removeTodo = (removedTodo) => {
        const index = removedTodo.detail.index
        dispatch('remove',{
            index: index
        });
    }
</script>
<Row>
{#each todos as todo, index}
    <TodoListItem todo="{todo}" index="{index}" on:checkClicked={updateCheck} on:removeClicked={removeTodo}></TodoListItem>
{/each}
</Row>
