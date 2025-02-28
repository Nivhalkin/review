<template>
    <section class="lookfor">
        <h3 class="lookfor__title">
            <CommunInlineText v-for="item in title" :key="item.text" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </h3>
        <p class="lookfor__description">
            <CommunInlineText v-for="item in description" :key="item.text" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </p>
        <section class="lookfor-list">
            <div v-for="item in list" :key="item.toString()">
                <div class="lookfor-list-item">
                    <figure class="lookfor-list-item__img">
                        <IconsChecked2 :currentColor="iconsColor" />
                    </figure>
                    <h4>
                        <CommunInlineText v-for="description in item.title" :key="description.text" :text="description.text"
                            :isBold="description.isBold" :textColor="description.textColor"
                            :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                            :link="description.link" />
                    </h4>
                </div>
                <p class="lookfor-list__description">
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
.lookfor {
    padding: 50px 46px 72px 34px;
    width: 100%;
    background: var(--lookfor-background-color);
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
        margin-bottom: 48px;
        font-size: var(--paragraph-font-size);
        text-align: center;
        padding: 0 40px;
    }

    &-list {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-column-gap: 74px;
        grid-row-gap: 34px;

        &-item {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 7px;
            font-size: 20px;

            &__img {
                width: 40px;
                height: 40px;
                margin-right: 10px;
            }
        }

        &__item {
            display: flex;
        }

        &__description {
            text-align: center;
            font-size: var(--paragraph-font-size);
        }
    }

    @media (max-width: 1024px) {
        padding: 20px 16px 36px 16px;

        &__title {
            text-align: center;
        }

        &__description {
            margin-bottom: var(--title-margin-bottom);
            padding: 0;
        }

        &-list {
            grid-template-columns: repeat(1, 1fr);
            grid-row-gap: 16x;

            &-item {
                font-size: 17px;

                &__img {
                    width: 28px;
                    height: 28px;
                    margin-right: 5px;
                }
            }
        }
    }
}
</style>