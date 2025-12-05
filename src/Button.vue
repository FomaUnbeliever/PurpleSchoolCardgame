<script setup>

</script>
<template>
    <button class="button">
        <div>
            <slot name="icon" />
            <slot name="text" />
        </div>
        <slot />
    </button>
</template>

<style scoped>
    .button {
        border: none;
        text-rendering: var(--text-color);
        border-radius: 100px;
        background: var(--color-bg);
        padding: 14px;
        font-family: var(--font);
        font-size: 20px;
        font-weight: 600;
        color: var(--text-color);
        cursor: pointer;
 
         
    }
</style>