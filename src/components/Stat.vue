<script setup>
defineProps({
  label: String,
  stat: String
})
</script>

<template>
  <div class="stat">
    <span class="stat__label">{{ label }}</span>
    <span class="stat__value">{{ stat }}</span>
  </div>
</template>

<style scoped>
.stat {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: var(--color-contrast-bg, #f4f6f8);
  padding: 15px 30px;
  border-radius: 12px;
  margin-bottom: 10px;
}
.stat__label {
  font-size: 18px;
  color: #555;
  font-weight: 500;
}
.stat__value {
  font-size: 18px;
  color: #222;
  font-weight: 700;
}
</style>