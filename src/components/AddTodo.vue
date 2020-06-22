<template>
    <li>
        <form @submit.prevent="onSubmit">
            <div class="input-group">
                <input class="form-control"
                       v-model="title"
                       placeholder="Добавить задачу"
                />
                <button class="ml-3 btn btn-outline-success"
                        type="submit"
                >&#10010;</button>
            </div>
        </form>
    </li>
</template>

<script>
    export default {
        name: "AddTodo",
        data() {
            return {
                title: ''
            }
        },
        methods: {
            onSubmit(){
                if ( this.title.trim() ) {
                    const newTodo = {
                        id: Date.now(),
                        title: this.title,
                        complited: false
                    };
                    this.$emit('add-todo', newTodo);
                    this.title = '';
                }
            }
        }
    }
</script>

<style scoped>

</style>