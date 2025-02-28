<template>
    <section class="highlight--split" :style="{
        '--list-header-background-color': threeSideList.headerBackgroundColor,
        '--list-header-title-color': threeSideList.titleColor
    }">
        <ContentHighlightSectionSmall v-for="item in threeSideList.listItem" :key="item.title" :title="item.title"
            :list="item.list" />
    </section>
</template>

<script setup lang="ts">
defineProps<{
    threeSideList: {
        listItem: { title: string; list: string[] }[];
        titleColor: string;
        headerBackgroundColor: string;
    }
}>()
</script>

<style lang="scss" scoped>
.highlight {
    &--split {
        display: flex;
        gap: 3px;
        margin-bottom: 20px;
        flex-wrap: wrap;
        overflow: hidden;
        border-radius: 5px;
        row-gap: 10px;

        * {
            min-width: fit-content;
        }

        :nth-child(1) {
            flex: 1;
        }

        :nth-child(2) {
            flex: 2;
        }

        :nth-child(3) {
            flex: 3;
        }

        @media (max-width: 1024px) {
            flex-direction: column;
            gap: 10px;
            border-radius: 0px;
        }
    }
}
</style>