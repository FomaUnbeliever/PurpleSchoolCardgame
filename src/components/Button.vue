<script setup>
defineOptions({
  inheritAttrs: true,
})
</script>

<template>
  <button class="button" v-on="$attrs">
    <slot></slot>
  </button>
</template>

<style scoped>
.button {
    border: none;
    border-radius: 13px;
    background: var(--gradient);
    padding: 14px;
    font-family: var(--font);
    font-size: 20px;
    font-weight: 600;
    color: var(--primary);
    cursor: pointer;
    display: flex;
    gap: 9px;
    align-items: center;
}
.button:hover{
    background: var(--gradient-inverted);
}
</style>