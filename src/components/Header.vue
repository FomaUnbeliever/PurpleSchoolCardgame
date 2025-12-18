<!-- src/components/Header.vue -->
<template>
  <header class="header">
    <Score :score="score" />
  </header>
</template>

<script setup>
import Score from './Score.vue'

defineProps({
  score: {
    type: Number,
    required: true
  }
})
</script>

<style scoped>
.header {
  padding: 1rem;
  background-color: #f5f5f5;
  border-bottom: 1px solid #ccc;
}
</style>