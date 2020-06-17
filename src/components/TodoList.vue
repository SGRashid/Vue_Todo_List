<template>
    <div class="todoList d-flex flex-column">
        <ul class="mx-auto d-flex flex-column align-items-start">
            <TodoItem v-for="todo in todos"
                      v-bind:todo="todo"
                      :key="todo.id"
            />
        </ul>
    </div>
</template>

<script>
    import TodoItem from '@/components/TodoItem';
    export default {
        props: ['todos'],
        components: {
            TodoItem
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