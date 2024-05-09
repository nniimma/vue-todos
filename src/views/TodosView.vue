<script setup>
  import TodoItem from '@/components/TodoItem.vue';
  import TodoCreater from '@/components/TodoCreater.vue';
  import { uid } from 'uid';
  import { ref } from 'vue';

  const todoList = ref([]);

  const createTodo = (todo) => {
    todoList.value.push({
      id: uid,
      todo,
      isCompleted: null,
      isEdited: null
    })
  }
</script>

<template>
  <main>
    <h1>Create todo:</h1>
    <todo-creater @create-todo="createTodo" />

    <ul>
      <todo-item v-for="todo in todoList" :todo="todo"/>
    </ul>
  </main>
</template>

<style lang="scss" scoped>
  @import '../assets/css/todo-view.scss';
</style>
