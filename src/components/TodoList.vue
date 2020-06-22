<template>
    <div class="todoList d-flex flex-column">
        <ul class="mx-auto d-flex flex-column align-items-start">
            <TodoItem v-for="todo in todos"
                      v-bind:todo="todo"
                      :key="todo.id"
                      v-on:remove-todo="removeTodo($event)"
            />
            <li>
                <div class="input-group">
                    <input class="form-control"
                           v-model="newTodo"
                           placeholder="Добавить задачу"
                    />
                    <button class="ml-3 btn btn-outline-success">&#10010;</button>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    import TodoItem from '@/components/TodoItem';
    export default {
        props: ['todos'],
        components: {
            TodoItem
        },
        data() {
            return {
                newTodo: ''
            }
        },
        methods: {
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