
<template>
    <section class="introduction">
        <header class="introduction-header">
            <figure class="introduction-header__avatar">
                <nuxt-img format="webp" class="introduction-header__avatar__img" alt="product image"
                width="41" height="41"
                    :src="`/images/article/avatar/avatar-${avatar}.png`" />
            </figure>
            <div class="introduction-header-info">
                <p class="introduction-header-info__author">
                    <CommunInlineText v-for="item in writtenBy" :key="item.text" :text="item.text" :isBold="item.isBold"
                        :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                        :link="item.link" />
                </p>
                <p class="introduction-header-info__date">
                    {{ date }}
                </p>
            </div>
        </header>

        <section class="introduction-section">
            <h3 class="introduction__title">
                {{ section1title }}
            </h3>
            <p class="introduction__paragraph" v-for="item in section1Descriptions" :key="item.toString()">
                <CommunInlineText v-for="description in item.paragraph" :key="description.text" :text="description.text"
                    :isBold="description.isBold" :textColor="description.textColor"
                    :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                    :link="description.link" />
            </p>
        </section>
        <section>
            <h3 class="introduction__title">
                {{ section2title }}
            </h3>
            <p class="introduction__paragraph" v-for="item in section2Descriptions" :key="item.toString()">
                <CommunInlineText v-for="description in item.paragraph" :key="description.text" :text="description.text"
                    :isBold="description.isBold" :textColor="description.textColor"
                    :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                    :link="description.link" />
            </p>

            <ul class="introduction-list">
                <li v-for="description in section2List" :key="description.text">
                    <span :style="{ 'font-weight': 'bold' }">- </span>
                    <CommunInlineText :text="description.text" :isBold="description.isBold"
                        :textColor="description.textColor" :highlightColor="description.highlightColor"
                        :isUnderlined="description.isUnderlined" :link="description.link" />
                </li>
            </ul>
        </section>
    </section>
</template>

<script setup lang="ts">
import InlineTextInterface from '@/types/InlineTextInterface';

defineProps<{
    avatar: number, writtenBy: InlineTextInterface[], date: string,
    section1title: string, section1Descriptions: { paragraph: InlineTextInterface[] }[],
    section2title: string,
    section2Descriptions: { paragraph: InlineTextInterface[] }[],
    section2List: InlineTextInterface[],
}>()

</script>

<style scoped lang="scss">
.introduction {
    padding: 54px;
    width: 100%;
    background: var(--introduction-background-color);
    border-radius: 6px;

    &-header {
        display: flex;
        align-items: center;
        margin-bottom: 9px;

        &__avatar {
            overflow: hidden;
            border-radius: 50%;
            margin-right: 19px;
            height: 41px;
            width: 41px;
        }
    }

    &__title {
        font-size: var(--title-font-size);
        font-weight: 700;
        margin-bottom: var(--title-margin-bottom);
    }

    &__paragraph {
        font-size: var(--paragraph-font-size);
        margin-bottom: 20px;

        &:last-child {
            margin-bottom: 0;
        }
    }

    &-section {
        margin-bottom: var(--title-margin-bottom);

        &:last-child {
            margin-bottom: 0;
        }
    }

    &-list {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-column-gap: 160px;
        grid-row-gap: 15px;
    }

    @media (max-width: 1024px) {
        padding: 16px;

        &-header {
            &__avatar {
                margin-right: 10px;
            }

            &-info {
                font-size: 12px;
            }
        }

        &-section {
            margin-bottom: 24px;

        }

        &-list {
            display: grid;
            grid-template-columns: repeat(1, 1fr);
            grid-row-gap: 15px;
        }

    }
}
</style>