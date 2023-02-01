<script>
    import { createEventDispatcher } from 'svelte';
    import {Input, Button, FormGroup, Label, Form} from 'sveltestrap';

    let defaultTodo = {
        title: '',
        description: '',
        isChecked: false
    };
    let todo = {
        ...defaultTodo
    }
    const dispatch = createEventDispatcher();
    const addTodo = () => {
        dispatch('add', {
            todo: todo
        });
        clearTodo()
    }
    const clearTodo = () => {
        todo = {...defaultTodo};
        document.getElementById('todoTitle').focus()
    }
    $: disable = !todo.title
</script>
<Form>
<FormGroup>
    <Label for="title">
        Title:
    </Label>
    <Input bind:value={todo.title} id="todoTitle" name="title"></Input>
</FormGroup>
<FormGroup>
    <Label for="description">
        Description:
    </Label>
    <Input name="description" type="textarea" bind:value={todo.description}>
    </Input>
</FormGroup>
</Form>
<Button color="primary" on:click={addTodo} disabled="{disable}">Add</Button>
<Button color="secondary" on:click={clearTodo} disabled="{disable}">Clear</Button>
