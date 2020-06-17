<template>
    <li class="d-flex justify-content-start align-items-center">
        <input type="checkbox" v-model="todo.complited"/>
        <strong class="ml-3">{{todo.id}}</strong>
        <span class="ml-3" v-if="!todo.complited">{{ todo.title }}</span>
        <span class="ml-3" v-else style="text-decoration: line-through">{{ todo.title }}</span>
        <button class="ml-auto">X</button>
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
</style>