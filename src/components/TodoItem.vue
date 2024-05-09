<template>
    <li>
        <input type="checkbox" :checked="todo.isCompleted">
        <div class="todo">
            <input v-if="isEdited" type="text" :value="todo.todo">
            <span v-else>
                {{ todo.todo }}
            </span>
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
        }
        })
</script>
<style lang="scss" scoped>
    @import '../assets/css/todo-item.scss';
</style>