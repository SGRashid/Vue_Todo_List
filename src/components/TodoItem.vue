<template>
    <li>
        <input type="checkbox" v-model="todo.complited"/>
        <span v-if="!todo.complited">{{ todo.title }}</span>
        <span v-else style="text-decoration: line-through">{{ todo.title }}</span>
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