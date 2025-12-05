<script setup>
import Button from './Button.vue';
</script>

<template>
  <main class="main">
    <Button>Нажми на меня</Button>
  </main>
</template>

<style scoped>
  .main{
    background: var(--color-bg-main);
    padding: 60px 50px;
    border-radius: 25px;
  }
</style>