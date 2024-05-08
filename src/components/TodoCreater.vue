<template>
    <div class="input-wrap">
        <input type="text" v-model="todo">
        <button style="cursor: pointer;" @click="createTodo()">Create</button>
    </div>
    {{ todo }}
</template>

<script setup>
    import { ref, defineEmits } from "vue";
    // emit is used to send variable to parent component
    const emit = defineEmits(["create-todo"])

    // the type of data in ref method can be string
    // to get the value in script we need to use value: console.log(todo.value)
    // in template . value will be added automatically
    const todo = ref('test')

    const createTodo = () => {
        emit("create-todo", todo.value);
    }

</script>

<style lang="scss" scoped>
@import '../assets/css/todo-create.css';
</style>