<template>
    <button type="button" class="button" @click="scrollToTop()">
        {{ props.text }}
    </button>
    <div>

    </div>
</template>

<script setup lang="ts">
const scrollToTop = () => window.scrollTo({ top: 0, behavior: 'smooth' })

const props = defineProps<{ text: string }>();
</script>

<style scoped lang="scss">
.button {
    font-size: 20px;
    margin: auto;
    display: flex;
    text-decoration: underline;
    background: transparent;

    @media (max-width: 1024px) {
        font-size: 12px;
    }
}
</style>