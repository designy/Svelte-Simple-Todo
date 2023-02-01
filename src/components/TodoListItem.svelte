<!-- 4. Have a single item here -->

<!-- 4-1. Create a UI with checkbox, text and delete button (get text through props) -->
<!-- 4-2. get todos array form top through props -->
<!-- 4-3. emit toggle and delete events to top -->

<script>
    import { createEventDispatcher } from 'svelte';
    import {Input, Button, Col, Card, CardHeader, CardTitle, CardBody, Label} from 'sveltestrap';

    const dispatch = createEventDispatcher();
    export let todo;
    export let index;
    const checkClicked = () => {
        dispatch('checkClicked', {
            todo: todo,
            index: index
        });
    }
    const removeClicked = () => {
        dispatch('removeClicked', {
            index: index
        });
    }
</script>
<Col md={{ size: 4 }}>
    <Card class="mb-3">
        <CardHeader>
            <CardTitle>
                {todo.title}
            </CardTitle>
        </CardHeader>
        <CardBody>
            <div class="d-flex">
                <Input id="todo-check{index}" type="checkbox" bind:checked={todo.isChecked} on:change={checkClicked}></Input>
                <Label for="todo-check{index}" style="text-decoration: {todo.isChecked ? 'line-through' : 'initial'};">{todo.description}</Label>
            </div>
            <Button color="danger" on:click={removeClicked}>Delete!</Button>
        </CardBody>
    </Card>
</Col>
