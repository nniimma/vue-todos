<template>
    <li>
        <input :id="'input-'+ index" type="checkbox" :checked="todo.isCompleted" @input="$emit('toggle-complete', index)">
        <div class="todo">
            <input v-if="isEdited" type="text" :value="todo.todo">
            <label v-else :for="'input-'+ index" :class="{'completed-todo' : todo.isCompleted}">
                {{ todo.todo }}
            </label>
        </div>
        <div class="todo-actions">
            <img v-if="isEdited" class="icon" src="../assets/icons/check-circle.svg" alt="">
            <img v-else class="icon" src="../assets/icons/pencil.svg" alt="">
            <img class="icon" src="../assets/icons/trash.svg" alt="">
        </div>
    </li>
</template>
<script setup>

    const props = defineProps({
            todo: {
                type: Object,
                required: true,
            },
            index: {
                type: Number,
                required: true
            }
        })

        defineEmits(['toggle-complete'])
</script>
<style lang="scss" scoped>
    @import '../assets/css/todo-item.scss';
</style>