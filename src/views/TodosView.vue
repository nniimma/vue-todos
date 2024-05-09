<script setup>
  import TodoItem from '@/components/TodoItem.vue';
  import TodoCreater from '@/components/TodoCreater.vue';
  import { uid } from 'uid';
  import { ref } from 'vue';

  const todoList = ref([]);

  const createTodo = (todo) => {
    const uniqueId = uid()
    todoList.value.push({
      id: uniqueId,
      todo,
      isCompleted: null,
      isEdited: null
    })
  }

  const toggleTodoComplete = (todoPos) => {
    todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
  }

  const toggleEditTodo = (todoPos) => {
    todoList.value[todoPos].isEdited = !todoList.value[todoPos].isEdited;
  }

  const updateTodo = (todoVal, todoPos) => {
    todoList.value[todoPos].todo = todoVal;
  }

  const deleteTodo = (todoId) => {
    // console.log(todoId)
    todoList.value = todoList.value.filter((todo) => todo.id !== todoId)
  }
</script>

<template>
  <main>
    <h1>Create todo:</h1>
    <todo-creater @create-todo="createTodo" />

    <ul class="todo-list" v-if="todoList.length > 0">
      <todo-item v-for="(todo, index) in todoList" 
      :todo="todo" :index="index" 
      @toggle-complete="toggleTodoComplete" 
      @edit-todo="toggleEditTodo"
      @update-todo="updateTodo"
      @delete-todo="deleteTodo"/>
    </ul>
    <p class="todos-msg" v-else>
      <span>You have no todos to complete, add one!</span>
    </p>
  </main>
</template>

<style lang="scss" scoped>
  @import '../assets/css/todo-view.scss';
</style>
