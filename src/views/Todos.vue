<template>
    <div>
        <h2>Todo app</h2>
        <hr>
        <Loader v-if="loading" />
        <template v-else>
            <select v-model="filter" class="custom-select col-md-2 mb-4">
                <option value="all">All</option>
                <option value="complited">Complited</option>
                <option value="not-complited">Not complited</option>
            </select>
            <TodoList v-bind:todos="filtredTodos"
                      v-on:remove-todo="removeTodo"
                      v-on:add-todo="addTodo"
            />
        </template>
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
                loading: true,
                filter: 'all'
            }
        },
        computed: {
            filtredTodos() {
                if (this.filter === 'complited') return this.todos.filter(t => t.complited);
                if (this.filter === 'not-complited') return this.todos.filter(t => !t.complited);
                return this.todos;
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