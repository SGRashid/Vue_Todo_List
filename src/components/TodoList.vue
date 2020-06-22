<template>
    <div class="todoList d-flex flex-column">
        <ul class="mx-auto d-flex flex-column align-items-start">
            <TodoItem v-for="todo in todos"
                      v-bind:todo="todo"
                      :key="todo.id"
                      v-on:remove-todo="removeTodo($event)"
            />
            <add-todo @add-todo="addTodo"></add-todo>
        </ul>
    </div>
</template>

<script>
    import TodoItem from '@/components/TodoItem';
    import AddTodo from '@/components/AddTodo';
    export default {
        props: ['todos'],
        components: {
            TodoItem,
            AddTodo
        },
        data() {
            return {
                newTodo: ''
            }
        },
        methods: {
            addTodo(todo) {
                console.log(todo);
                this.$emit('add-todo', todo);
            },
            removeTodo(id) {
                this.$emit('remove-todo', id);
            }
        }
    }
</script>
<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>