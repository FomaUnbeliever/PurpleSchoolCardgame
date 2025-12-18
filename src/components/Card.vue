<!-- src/components/Card.vue -->
<template>
  <div class="card" @click="flip">
    <div v-if="state === 'closed'" class="card-face card-front">?</div>
    <div v-else class="card-face card-back">
      {{ word }} — {{ translation }}
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  word: { type: String, required: true },
  translation: { type: String, required: true },
  state: { type: String, default: 'closed' } // 'closed' | 'opened'
})

const emit = defineEmits(['update-state'])

function flip() {
  if (props.state === 'closed') {
    emit('update-state', 'opened')
  } else {
    emit('update-state', 'closed')
  }
}
</script>

<style scoped>
.card {
  width: 120px;
  height: 160px;
  border: 2px solid #444;
  border-radius: 8px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  background: #fff;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
}

.card-face {
  text-align: center;
  padding: 10px;
}
</style>