<template>
    <li class="d-flex justify-content-start align-items-center w-100">
        <input type="checkbox" v-model="todo.complited"/>
        <strong class="ml-3">{{index + 1}}</strong>
        <span class="ml-3 text-left" v-bind:class="{complited: todo.complited}">{{ todo.title | uppercase }}</span>
        <button class="btn btn-outline-danger border-0 ml-auto"
                v-on:click="$emit('remove-todo', todo.id)"
        >&#10006;</button>
    </li>
</template>
<script>
export default {
   props: {
       todo: {
           type: Object,
           required: true
       },
       index: Number
   },
    filters: {
       uppercase(value) {
           return value.toUpperCase();
       }
    }
}
</script>
<style>
    li {
        max-width: 600px;
    }
    .complited { text-decoration: line-through; }
</style>