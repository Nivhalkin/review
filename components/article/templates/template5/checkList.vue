<template>
    <section class="checkList">
        <h3 class="checkList__title">
            <CommunInlineText v-for="item in title" :key="item.text" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </h3>
        <p class="checkList__description">
            <CommunInlineText v-for="item in description" :key="item.text" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </p>
        <section class="checkList-list">
            <div v-for="item in list" :key="item.toString()">
                <div class="checkList-list-item">
                    <figure class="checkList-list-item__img">
                        <IconsChecked3 :currentColor="iconsColor" />
                    </figure>
                    <h4>
                        <CommunInlineText v-for="description in item.title" :key="description.text" :text="description.text"
                            :isBold="description.isBold" :textColor="description.textColor"
                            :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                            :link="description.link" />
                    </h4>
                </div>
                <p class="checkList-list__description">
                    <CommunInlineText v-for="description in item.description" :key="description.text"
                        :text="description.text" :isBold="description.isBold" :textColor="description.textColor"
                        :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                        :link="description.link" />
                </p>

            </div>
        </section>
    </section>
</template>

<script setup lang="ts">
import InlineTextInterface from "~/types/InlineTextInterface";

defineProps<{
    title: InlineTextInterface[],
    description: InlineTextInterface[],
    iconsColor: string,
    list: { title: InlineTextInterface[], description: InlineTextInterface[] }[],
}>()
</script>

<style scoped lang="scss">
.checkList {
    padding: 72px 47px 48px 67px;
    width: 100%;
    background: var(--checkList-background-color);
    border-radius: 6px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    &__title {
        font-size: var(--title-font-size);
        font-weight: 700;
        margin-bottom: var(--title-margin-bottom);
    }

    &__description {
        margin-bottom: 20px;
        font-size: var(--paragraph-font-size);
    }

    &-list {
        padding: 35px;
        border-radius: 6px;
        border: 1px solid var(--checkList-list-border-color);
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        gap: 20px;

        &-item {
            display: flex;
            align-items: center;
            margin-bottom: 9px;
            font-size: 16px;

            &__img {
                margin-right: 10px;
            }
        }

        &__item {
            display: flex;
        }

        &__description {
            padding-left: 35px;
            text-align: left;
            font-size: var(--paragraph-font-size);
        }
    }

    @media (max-width: 1024px) {
        padding: 20px 16px;

        &__description {
            margin-bottom: 16px;
        }

        &-list {
            padding: 16px;
        }
    }
}
</style>