<script>
    import TodoForm from "./TodoForm.svelte";
    import TodoList from "./TodoList.svelte";
    import { Row, Col, Container } from 'sveltestrap';

    let todos = []
    const addTodo = (addedTodo) => {
        todos = [...todos, addedTodo.detail.todo]
    }
    const removeTodo = (removedTodo) => {
        const index = removedTodo.detail.index;
        todos.splice(index, 1);
        todos = [...todos ]
    }
    const updateTodo = (updatedTodo) => {
        todos[updatedTodo.index] = updatedTodo.todo
        todos = [...todos]
    }
</script>
<Container>
    <Row class="mb-5">
        <Col sm="12" md={{ size: 6, offset: 3 }}>
            <h1>The Todo component!🍔
            </h1>
            <TodoForm on:add={addTodo}></TodoForm>
        </Col>
    </Row>
</Container>
<Container fluid>
    <TodoList todos={todos} on:update={updateTodo} on:remove={removeTodo}> </TodoList>
</Container>
