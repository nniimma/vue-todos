<script setup>
  import TodoItem from '@/components/TodoItem.vue';
  import TodoCreater from '@/components/TodoCreater.vue';
  import { uid } from 'uid';
  import { ref, watch, computed } from 'vue';

  const todoList = ref([]);

  // watch do the function eachtime that the values inside todoList changes:
  // it takes the new value and the old value of the list
  // we use deep property becaue inside the array we have object, so it should go depper inside to get the values inside the object
  watch(todoList, (newValue, oldValue) => {
    setTodoListLocalStorage()
  }, {
    deep: true,
  })

  // in computed each time the value is updated, it will execute again.
  const todoCompleted = computed(() => {
    return todoList.value.every((todo) => todo.isCompleted)
  })

  const setTodoListLocalStorage = () => {
    localStorage.setItem('todoList', JSON.stringify(todoList.value))
  }

  const fetchTodoList = () => {
    const savedTodoList = JSON.parse(localStorage.getItem('todoList'));
    if(savedTodoList){
      todoList.value = savedTodoList
    }
  }

  fetchTodoList()

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
    <p v-if="todoCompleted && todoList.length > 0" class="todos-msg">You have completed all of your todos.</p>
  </main>
</template>

<style lang="scss" scoped>
  @import '../assets/css/todo-view.scss';
</style>
