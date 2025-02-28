<template>
    <section class="sources">
        <h4 class="sources__title">
            <CommunInlineText v-for="item in title" :key="item.toString()" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </h4>

        <p class="sources__link" v-for="(item, index) in items" :key="item.text">
            <CommunInlineText :text="`${index + 1}. ${item.text}`" :isBold="item.isBold" :textColor="item.textColor"
                :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined" :link="item.link" />
        </p>
    </section>
</template>

<script setup lang="ts">
import InlineTextInterface from "~/types/InlineTextInterface";

defineProps<{
    title: InlineTextInterface[],
    items: InlineTextInterface[]
}>()
</script>

<style lang="scss" scoped>
.sources {
    &__title {
        font-size: 18px;
        font-weight: 700;
        margin-bottom: 13px;
    }

    &__link {
        margin-bottom: 13px;
        font-size: 14px;
        font-weight: 500;

        &:last-child {
            margin-bottom: 0px;
        }
    }

    @media (max-width: 1024px) {
        padding: 0 18px;
        &__link {
            font-size: 10px;
        }
    }

}
</style>