<template>
    <li>
        <input :id="'input-'+ index" type="checkbox" :checked="todo.isCompleted" @input="$emit('toggle-complete', index)">
        <div class="todo">
            <input v-if="todo.isEdited" type="text" :value="todo.todo" @input="$emit('update-todo', $event.target.value, index)">
            <label v-else :for="'input-'+ index" :class="{'completed-todo' : todo.isCompleted}">
                {{ todo.todo }}
            </label>
        </div>
        <div class="todo-actions">
            <img v-if="todo.isEdited" class="icon" src="../assets/icons/check-circle.svg" @click="$emit('edit-todo', index)">
            <img v-else class="icon" src="../assets/icons/pencil.svg" @click="$emit('edit-todo', index)">
            <img class="icon" src="../assets/icons/trash.svg" >
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

        defineEmits(['toggle-complete', 'edit-todo', 'update-todo'])
</script>
<style lang="scss" scoped>
    @import '../assets/css/todo-item.scss';
</style>