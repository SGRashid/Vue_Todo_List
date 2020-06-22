<template>
    <li class="d-flex justify-content-start align-items-center">
        <input type="checkbox" v-model="todo.complited"/>
        <!--<strong class="ml-3">{{todo.id}}</strong>-->
        <span class="ml-3" v-bind:class="{complited: todo.complited}">{{ todo.title }}</span>
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
       }
   }
}
</script>
<style>
    li {
        width: 300px;
    }
    .complited { text-decoration: line-through; }
</style>