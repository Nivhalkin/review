<template>
    <div class="linear" :style="{
        '--percentage-background': `${percentage}%`
    }">
        <div class="linear-filled">
            <slot></slot>
        </div>
    </div>
</template>

<script setup lang="ts">
defineProps<{ percentage: number }>()
</script>

<style scoped lang="scss">
.linear {
    position: relative;
    width: 100%;
    height: 27px;
    border-radius: 10px;
    background-color: #F3F3F3;
    overflow: hidden;

    &-filled {
        position: absolute;
        height: 100%;
        left: 0;
        top: 0;
        background-color: var(--linear-filled-color);
        width: var(--percentage-background);
        display: flex;
        align-items: center;
    }
}
</style>