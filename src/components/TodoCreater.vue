<template>
    <div class="input-wrap">
        <input type="text" v-model="todo">
        <button>Create</button>
    </div>
    {{ todo }}

    <div class="input-wrap">
        <input type="text" v-model="todoState.todo">
        <button>Create</button>
    </div>
    {{ todoState.todo }}
</template>

<script setup>
    import { reactive, ref } from "vue";

    // the type of data in ref method can be string
    // to get the value in script we need to use value: console.log(todo.value)
    // in template . value will be added automatically
    const todo = ref('test')

    // in reactive method the value should be object it can't be primative value like string
    const todoState = reactive({
        todo: 'testing'
    })
</script>

<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
      outline: none;
    }
  }

  button {
    padding: 8px 16px;
    border: none;
  }
}
</style>