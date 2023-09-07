<script setup>
import Menu from './components/Menu.vue';
import Home from './components/Home.vue';
</script>

<template>
<Menu />

<main>
  <router-view></router-view>
</main>
</template>
