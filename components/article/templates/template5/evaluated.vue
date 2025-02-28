<template>
    <section class="evaluated">
        <h3 class="evaluated__title">
            <CommunInlineText v-for="item in title" :key="item.text" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </h3>

        <section class="evaluated-list">
            <div v-for="item in list" :key="item.imageUrl" class="evaluated-list-item">
                <figure class="evaluated-list-item__img">
                    <nuxt-img height="62" width="62" alt="icon"  class="evaluated-list-item__img-image" :src="`/images/icons/${item.imageUrl}`" />
                </figure>
                <p class="evaluated-list-item__text">
                    <CommunInlineText v-for="subItem in item.text" :key="subItem.text" :text="subItem.text"
                        :isBold="subItem.isBold" :textColor="subItem.textColor" :highlightColor="subItem.highlightColor"
                        :isUnderlined="subItem.isUnderlined" :link="subItem.link" />
                </p>
            </div>
        </section>
    </section>
</template>

<script setup lang="ts">
import InlineTextInterface from "~/types/InlineTextInterface";

defineProps<{
    title: InlineTextInterface[],
    list: { imageUrl: string, imageColor: string, text: InlineTextInterface[] }[],
}>()
</script>

<style lang="scss" scoped>
.evaluated {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    &__title {
        font-size: var(--title-font-size);
        font-weight: 700;
        margin-bottom: var(--title-margin-bottom);
    }

    &-list {
        display: flex;
        justify-content: center;
        align-items: center;

        &-item {
            display: flex;
            align-items: center;
            flex-direction: column;
            margin-right: 100px;

            &__img {
                height: 62px;
                width: inherit;
                margin-bottom: 10px;

                &-image {
                    height: 100%;
                }
            }

            &__text {
                font-size: 15px;
                font-weight: 600;
            }

            &:last-child {
                margin-right: 0;
            }
        }
    }

    @media (max-width: 1024px) {
        &-list {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            grid-column-gap: 50px;
            grid-row-gap: 20px;

            &-item {
                margin-right: 0;
                

                &__img {
                    height: 50px;
                    width: inherit;

                    &-image {
                        width: auto;
                    }
                }
            }
        }
    }
}
</style>