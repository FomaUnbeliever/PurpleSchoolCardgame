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
import { ref } from 'vue'
import Header from './components/Header.vue'
import Card from './components/Card.vue'

const score = ref(10)

const cards = ref([
  {
    word: 'car',
    translation: 'автомобиль',
    state: 'closed',
    status: 'pending'
  },
  {
    word: 'dog',
    translation: 'собака',
    state: 'opened',
    status: 'success'
  },
  {
    word: 'cat',
    translation: 'кот',
    state: 'opened',
    status: 'fail'
  },
  {
    word: 'bus',
    translation: 'автобус',
    state: 'closed',
    status: 'pending'
  }
])
</script>

<style>
.cards-container {
  padding: 20px;
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}
</style>