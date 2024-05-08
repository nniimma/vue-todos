<template>
    <div class="input-wrap" :class="{'input-err' : todoState.invalid}">
        <input type="text" v-model="todoState.todo">
        <todo-button @click="createTodo">
            <template #create-btn> <!--! instead of #create-btn we can use v-slot:create-btn -->
                    Create
            </template>
        </todo-button>
    </div>
    <!-- v-if doesn't put the tag in the DOM if the statement is false but v-show will put it there with display none... -->
    <p v-show="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</p>
</template>

<script setup>
    import { ref, defineEmits, reactive } from "vue";
    import TodoButton from "./TodoButton.vue";
    
    // emit is used to send variable to parent component
    const emit = defineEmits(["create-todo"])

    const todoState = reactive({
        todo: '',
        invalid: null,
        errMsg: ''
    });

    const createTodo = () => {
        todoState.invalid = null;
        if(todoState.todo !==''){
            emit("create-todo", todoState.todo);
            todoState.todo = '';
            return
        }
        todoState.invalid = true;
        todoState.errMsg = 'Todo value can not be empty!'
    }

</script>

<style lang="scss" scoped>
@import '../assets/css/todo-create.scss';
</style>