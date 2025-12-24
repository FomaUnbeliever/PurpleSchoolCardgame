<!-- src/components/Card.vue -->
<template>
  <div
    class="card"
    :class="{
      'card--closed': state === 'closed',
      'card--opened': state === 'opened',
      'card--pending': status === 'pending',
      'card--success': status === 'success',
      'card--fail': status === 'fail'
    }"
    @click="handleClick"
  >
    <div v-if="state === 'closed'" class="card-content">
      ?
    </div>
    <div v-else class="card-content">
      {{ word }} — {{ translation }}
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  word: { type: String, required: true },
  translation: { type: String, required: true },
  state: { type: String, default: 'closed' },       // 'closed' | 'opened'
  status: { type: String, default: 'pending' }      // 'pending' | 'success' | 'fail'
})

const emit = defineEmits(['update-state'])

function handleClick() {
  if (props.status !== 'success') {
    const newState = props.state === 'closed' ? 'opened' : 'closed'
    emit('update-state', newState)
  }
}
</script>

<style scoped>
.card {
  width: 120px;
  height: 160px;
  border: 2px solid #444;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
}

.card-content {
  text-align: center;
  padding: 10px;
}

/* Состояния стиля */

.card--pending {
  background-color: #fff;
  border-color: #999;
}

.card--success {
  background-color: #d4edda;
  border-color: #28a745;
  cursor: default;
}

.card--fail {
  background-color: #f8d7da;
  border-color: #dc3545;
}

.card--opened.card--success {
  box-shadow: 0 0 10px #28a745;
}

.card--opened.card--fail {
  box-shadow: 0 0 10px #dc3545;
}
</style>