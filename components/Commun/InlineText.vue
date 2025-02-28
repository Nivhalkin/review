<template>
    <span :style="{
        '--font-weight': isBold ? '700' : 'inherit',
        '--text-color': textColor,
        '--background-color': highlightColor ? highlightColor : 'transparent',
        '--underline': isUnderlined ? 'underline' : 'none'
    }" class="inline-text">
        <NuxtLink v-if="link.length > 0" :to="link">
            {{ text }}
        </NuxtLink>
        <template v-else>
            {{ text }}
        </template>

    </span>
</template>

<script setup lang="ts">
defineProps<{
    text: string;
    isBold: boolean;
    textColor: string;
    highlightColor: string;
    isUnderlined: boolean;
    link: string;
}>()
</script>

<style lang="scss" scoped>
.inline-text {
    font-weight: var(--font-weight);
    color: var(--text-color);
    background-color: var(--background-color);
    text-decoration: var(--underline);
    font-size: inherit;
    margin-right: 5px;

    a {
        color: var(--text-color);

        &:hover {
            cursor: pointer;
        }
    }

    &:last-child {
        margin-right: 0;
    }
}
</style>