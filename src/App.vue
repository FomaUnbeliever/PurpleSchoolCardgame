<!-- src/App.vue -->
<template>
  <Header :score="gameScore" />
  <div class="game-board">
    <Card
      v-for="(card, index) in cards"
      :key="index"
      :value="card.value"
      :status="card.status"
      @status-change="(newStatus) => updateCardStatus(index, newStatus)"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Card from './components/Card.vue'

const gameScore = ref(0)

const cards = ref([
  { value: 'A', status: 'closed' },
  { value: 'B', status: 'closed' },
  { value: 'A', status: 'closed' },
  { value: 'B', status: 'closed' }
])

function updateCardStatus(index, newStatus) {
  cards.value[index].status = newStatus
  // Можно добавить логику сравнения пар и обновления score
}
</script>

<style>
.game-board {
  display: flex;
  gap: 1rem;
  padding: 2rem;
}
</style>