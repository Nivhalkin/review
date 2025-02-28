<template>
    <span :style="{
        '--font-weight': fontWeight,
        '--text-color': textColor,
        '--background-color': highlightColor ? highlightColor : 'transparent',
        '--underline': isUnderlined ? 'underline' : 'none',
        '--font-style': isItalic ? 'italic' : 'normal',
        '--font-family': fontFamily,
        '--mobile-font-size': mobile.textSize,
        '--mobile-line-height': mobile.lineHeight,
        '--desktop-font-size': desktop.textSize,
        '--desktop-line-height': desktop.lineHeight,
    }" class="inline-text">
        <NuxtLink v-if="link?.length > 0" :to="link">
            {{ text }}
        </NuxtLink>
        <template v-else>
            {{ text }}
        </template>
    </span>
    <div :style="{ 'display': 'inline' }">&nbsp;</div>
</template>

<script setup lang="ts">
defineProps<{
    text: string;
    fontWeight: number;
    textColor: string;
    highlightColor: string;
    isUnderlined: boolean;
    link: string;
    fontFamily: string;
    isItalic: boolean;
    mobile: {
        textSize: string;
        lineHeight: string,
    };
    desktop: {
        textSize: string;
        lineHeight: string,
    }
}>()
</script>

<style lang="scss" scoped>
.inline-text {
    font-family: var(--font-family);
    font-weight: var(--font-weight);
    color: var(--text-color);
    background-color: var(--background-color);
    text-decoration: var(--underline);
    font-size: var();
    font-style: var(--font-style);
    font-size: var(--desktop-font-size);
    line-height: var(--desktop-line-height);

    @media (max-width: 1024px) {
        font-size: var(--mobile-font-size);
        line-height: var(--mobile-line-height);
    }


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