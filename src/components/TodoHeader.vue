<template>
    <header>
        <nav class="container">
            <div class="branding">
                <img src="../assets/Vue_Logo_Black.png" alt="">
                <h1>Vue Todos:</h1>
            </div>
            <ul class="nav-routes">
                <router-link to="/">Home</router-link>
                <router-link to="/about">About</router-link>
            </ul>
        </nav>
    </header>
</template>

<script setup>
    import { RouterLink } from 'vue-router';
</script>

<style lang="scss" scoped>
  @import '../assets/css/todo-header.css';
</style>