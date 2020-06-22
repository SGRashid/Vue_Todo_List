<template>
    <div>
        <h2>Todo app</h2>
        <hr>
        <Loader v-if="loading" />
        <TodoList v-else
                  v-bind:todos="todos"
                  v-on:remove-todo="removeTodo"
                  v-on:add-todo="addTodo"
        />
    </div>
</template>

<script>
    import TodoList from '@/components/TodoList';
    import Loader from '@/components/Loader';

    export default {
        name: 'Todos',
        data() {
            return {
                todos: [
                    { id: 0, title: 'Купить пиво', complited: true },
                    { id: 1, title: 'Купить чипсы', complited: false },
                    { id: 2, title: 'Купить табак для кальяна', complited: false },
                    { id: 3, title: 'Купить сосиски', complited: false },
                    { id: 4, title: 'Купить хлеб', complited: false },
                ],
                loading: true
            }
        },
        methods: {
            addTodo(todo){
                this.todos.push(todo);
            },
            removeTodo(id) {
                this.todos = this.todos.filter(todo => todo.id !== id);
                this.loading = false;
            }
        },
        mounted() {
            fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
                .then(response => response.json())
                .then(json => this.todos = json);
            setTimeout(() => this.loading = false, 500);
        },
        components: {
            Loader,
            TodoList
        },
    }
</script>

<style scoped>

</style>