<!-- src/components/Score.vue -->
<template>
  <div class="score">Score: {{ score }}</div>
</template>

<script setup>
defineProps({
  score: {
    type: Number,
    required: true
  }
})
</script>

<style scoped>
.score {
  font-size: 1.2rem;
  font-weight: bold;
}
</style>