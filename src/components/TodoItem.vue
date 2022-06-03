<template>
    <div :class="['todo-item', todoProps.completed ? 'is-completed' : '']" :id="new_id">
        <input type="checkbox" :checked="[todoProps.completed]">{{ todoProps.title }}
        <button class="del-btn">Delete</button>
    </div>    
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['todoProps'],
}
</script>

<style scoped>
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    margin: 0;
    border-bottom: 1px dotted #ccc;
}

.is-completed {
    text-decoration: line-through;
}

.del-btn {
    background: #ff0000;
    color: #fff;
    border: none;
    cursor: pointer;
    float: right;
}
</style>