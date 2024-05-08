<template>
    <button style="cursor: pointer;">
        <!-- if we define anything inside the slot will be as a default value and if we define a new value in the main page this one will be removed -->
        <slot name="create-btn"></slot>
    </button>
</template>
<script setup>

</script>
<style lang="scss" scoped>
      button {
    padding: 8px 16px;
    border: none;
  }
</style>