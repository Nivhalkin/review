<template>
    <div class="link-popup">
        {{ props.text }}
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{ text: string }>()
</script>

<style lang="scss" scoped>
.link-popup {
    position: relative;
    color: #FFF;
    font-size: 13px;
    padding: 5px 32px;
    z-index: 1;
    background: #525252;
    border-radius: 6px;

    &::after {
        content: '';
        background: #525252;
        position: absolute;
        width: 12px;
        height: 12px;
        left: 50%;
        bottom: 0;
        transform: translate(-50%, 50%) rotate(45deg);
    }

    @media (max-width: 1024px) {
        font-size: 10px;
        padding: 5px 8px;

        &::after {
            width: 8px;
            height: 8px;
        }
    }
}
</style>