<!-- src/App.vue -->
<template>
  <Header :score="score" />
  <div class="cards-container">
    <Card
      v-for="(card, index) in cards"
      :key="index"
      :word="card.word"
      :translation="card.translation"
      :state="card.state"
      :status="card.status"
      @update-state="newState => cards[index].state = newState"
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import Header from './components/Header.vue'
import Card from './components/Card.vue'

const score = ref(0)
const cards = ref([])

onMounted(async () => {
  try {
    const response = await axios.get('http://localhost:3001/cards')
    // Добавляем недостающие поля: state и status
    cards.value = response.data.map(item => ({
      ...item,
      state: 'closed',
      status: 'pending'
    }))
  } catch (error) {
    console.error('Ошибка при загрузке карточек:', error)
    // Фолбэк — если API не запущен
    cards.value = [
      { word: 'car', translation: 'автомобиль', state: 'closed', status: 'pending' }
    ]
  }
})
</script>

<style>
.cards-container {
  padding: 20px;
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}
</style>