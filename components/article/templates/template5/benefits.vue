<template>
    <section class="benefits">
        <header>
            <h3 class="benefits__title">
                <CommunInlineText v-for="item in section1title" :key="item.text" :text="item.text" :isBold="item.isBold"
                    :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                    :link="item.link" />
            </h3>
            <p class="benefits__subTitle">
                <CommunInlineText v-for="item in section1subTitle" :key="item.text" :text="item.text" :isBold="item.isBold"
                    :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                    :link="item.link" />
            </p>
        </header>
        <h3 class="benefits__title">
            <CommunInlineText v-for="item in section2title" :key="item.text" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </h3>
        <ul class="benefits-list">
            <li v-for="item in section2List" :key="item.text" class="benefits-list__item">
                <figure class="benefits-list__item__img">
                    <IconsChecked1 :currentColor="iconsColor" />
                </figure>

                <CommunInlineText :text="item.text" :isBold="item.isBold" :textColor="item.textColor"
                    :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined" :link="item.link" />
            </li>
        </ul>
    </section>
</template>

<script setup lang="ts">
import InlineTextInterface from "~/types/InlineTextInterface";

defineProps<{
    section1title: InlineTextInterface[],
    section1subTitle: InlineTextInterface[],
    section2title: InlineTextInterface[],
    section2List: InlineTextInterface[],
    iconsColor: string,
}>()

</script>

<style scoped lang="scss">
.benefits {
    padding: 54px;
    width: 100%;
    background: var(--benefits-background-color);
    border-radius: 6px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    &__title {
        margin-bottom: var(--title-margin-bottom);
        font-weight: 600;
        font-size: var(--title-font-size);
        text-align: center;
    }

    &__subTitle {
        font-size: var(--paragraph-font-size);
        font-weight: 400;
        text-align: center;
        margin-bottom: var(--title-margin-bottom);
    }

    &-list {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-column-gap: 30px;
        grid-row-gap: 20px;

        &__item {
            padding: 15px 10px;
            width: 100%;
            background-color: var(--benefits-list-item-background-color);
            border-radius: 30px;
            display: flex;
            align-items: center;

            &__img {
                margin-right: 10px;
            }
        }
    }

    @media (max-width: 1024px) {
        padding: 16px;

        &__title,
        &__subTitle {
            text-align: left;
        }

        &-list {
            display: grid;
            grid-template-columns: repeat(1, 1fr);
            grid-row-gap: 10px;
            width: 100%;

            &__item {
                padding: 10px 19px;
            }
        }
    }
}
</style>