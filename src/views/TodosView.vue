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

  const toggleTodoComplete = (todoPos) => {
    todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
  }
</script>

<template>
  <main>
    <h1>Create todo:</h1>
    <todo-creater @create-todo="createTodo" />

    <ul class="todo-list" v-if="todoList.length > 0">
      <todo-item v-for="(todo, index) in todoList" :todo="todo" :index="index" @toggle-complete="toggleTodoComplete"/>
    </ul>
    <p class="todos-msg" v-else>
      <span>You have no todos to complete, add one!</span>
    </p>
  </main>
</template>

<style lang="scss" scoped>
  @import '../assets/css/todo-view.scss';
</style>
