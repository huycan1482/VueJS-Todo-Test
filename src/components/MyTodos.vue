<template>
    <TodoItem v-for="todo in todos" v-bind:key="todo.id" v-bind:todoProps="todo" />
</template>

<script>
    import { ref } from 'vue'
    import TodoItem from './TodoItem.vue'

    export default {
        name: 'MyTodos',
        components: {TodoItem},
        setup() {
            const todos = ref([
                {
                    id: 1,
                    title: 'Viec 1',
                    completed: false,
                },
                {
                    id: 2,
                    title: 'Viec 2',
                    completed: false,
                },
                {
                    id: 3,
                    title: 'Viec 3',
                    completed: false,
                },
            ])

            return {
                todos 
            }
        }
    }
</script>

<style scoped>

</style>