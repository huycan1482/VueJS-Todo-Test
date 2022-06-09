<template>
    <AddTodo @add-todo="addTodo"/>
    <TodoItem v-for="todo in todos" v-bind:key="todo.id" v-bind:todoProps="todo" 
    @item-completed="markCompleted"
    @delete-item="deleteTodo"/>
    <!-- v-on:item-completed="markCompleted"/> -->
    <!-- <TodoItem v-for="todo in todos" v-bind:key="todo.id" v-bind:todoProps="todo"/> -->
</template>

<script>
    import { ref } from 'vue'
    // ref sử dụng cho trạng thái ban đầu
    import TodoItem from './TodoItem.vue'
    import AddTodo from './AddTodo.vue'
    // import {v4 as uuidv4} from 'uuid'
    import axios from 'axios'

    export default {
        name: 'MyTodos',
        components: {TodoItem, AddTodo},
        setup() {
            const todos = ref([]);

            const getAllTodos = async () => {
                try {
                    const res = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
                    todos.value = res.data
                } catch (error) {
                    console.log(error)
                }
            }

            getAllTodos()

            const markCompleted = id => {
                todos.value = todos.value.map( todo => {
                    if (todo.id == id) todo.completed = !todo.completed
                    return todo
                })
            }

            // const deleteTodo = id => {
            const deleteTodo = async id => {
                // todos.value = todos.value.filter(todo => todo.id !== id)
                // lọc to có id khác

                try {
                    await axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`);
                    todos.value = todos.value.filter(todo => todo.id !== id)
                } catch (error) {
                    console.log(error);
                }
            }

            const addTodo = async newTodo => {
                // todos.value.push(newTodo)
                try {
                    const rest = await axios.post(`https://jsonplaceholder.typicode.com/todos/`, newTodo)
                    todos.value.push(rest.data)
                } catch (error) {
                    console.log(error);
                }
            }

            return {
                todos,
                markCompleted,
                deleteTodo,
                addTodo, 
            }
        }
    }
</script>

<style scoped>

</style>