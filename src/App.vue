<template>
  <div id="app">
    <h1>Todo app</h1>
    <hr>
    <TodoList v-bind:todos="todos"
              v-on:remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList';

export default {
    name: 'App',
      data() {
        return {
            todos: [
                { id: 0, title: 'Купить пиво', complited: true },
                { id: 1, title: 'Купить чипсы', complited: false },
                { id: 2, title: 'Купить табак для кальяна', complited: false },
                { id: 3, title: 'Купить сосиски', complited: false },
                { id: 4, title: 'Купить хлеб', complited: false },
            ]
        }
      },
    components: {
      TodoList
    },
    methods: {
        removeTodo(id) {
            this.todos = this.todos.filter(todo => todo.id !== id);
        }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
