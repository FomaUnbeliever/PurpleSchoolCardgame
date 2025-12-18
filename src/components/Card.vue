<!-- src/components/Card.vue -->
<template>
  <div
    class="card"
    :class="{ flipped: isFlipped, matched: status === 'matched' }"
    @click="flip"
  >
    <div class="card-inner">
      <div class="card-front">?</div>
      <div class="card-back">{{ value }}</div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps, defineEmits } from 'vue'

const props = defineProps({
  value: { type: [String, Number], required: true },
  status: { type: String, default: 'closed' } // closed | opened | matched
})

const emit = defineEmits(['flip', 'status-change'])

const isFlipped = ref(props.status !== 'closed')

function flip() {
  if (props.status === 'matched') return

  const newStatus = isFlipped.value ? 'closed' : 'opened'
  isFlipped.value = !isFlipped.value
  emit('status-change', newStatus)
  emit('flip')
}
</script>

<style scoped>
.card {
  width: 80px;
  height: 100px;
  perspective: 600px;
  cursor: pointer;
}

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.card.flipped .card-inner {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid #333;
  backface-visibility: hidden;
  font-weight: bold;
}

.card-back {
  transform: rotateY(180deg);
  background: #fff;
}

.card.matched {
  opacity: 0.6;
  pointer-events: none;
}
</style>