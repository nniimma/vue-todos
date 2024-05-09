<template>
    
</template>
<script setup>
    // you can define probs as an array or an object
    // const props = defineProps(['todo'])
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