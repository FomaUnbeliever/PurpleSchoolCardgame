<!-- src/App.vue -->
<template>
  <Header :score="score" />
  <div style="padding: 20px; display: flex; gap: 1rem;">
    <!-- Выводим ТОЛЬКО ОДНУ карту (по заданию) -->
    <Card
      :word="card.word"
      :translation="card.translation"
      :state="card.state"
      @update-state="newState => card.state = newState"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Card from './components/Card.vue'

// Реактивный счёт
const score = ref(0)

// Одна карта (реактивная)
const card = ref({
  word: 'dog',
  translation: 'собака',
  state: 'closed',       // может быть 'opened'
  status: 'pending'      // пока не используем активно
})
</script>