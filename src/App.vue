<template>
  <div>Текущая дата: {{ currentDate }}</div>
</template>

<script setup>
import { ref } from 'vue'

const currentDate = ref(new Date().toLocaleDateString('ru-RU'))
</script>
