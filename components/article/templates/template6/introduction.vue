
<template>
    <section class="introduction">
        <header class="introduction-header">
            <figure class="introduction-header__avatar">
                <nuxt-img format="webp" width="41" height="41" class="introduction-header__avatar__img" alt="product image"
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
                {{ title }}
            </h3>
            <p class="introduction__paragraph" v-for="item in descriptions" :key="item.toString()">
                <CommunInlineText v-for="description in item.paragraph" :key="description.text" :text="description.text"
                    :isBold="description.isBold" :textColor="description.textColor"
                    :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                    :link="description.link" />
            </p>
        </section>
    </section>
</template>

<script setup lang="ts">
import InlineTextInterface from '@/types/InlineTextInterface';

defineProps<{
    avatar: number, writtenBy: InlineTextInterface[], date: string,
    title: string, descriptions: { paragraph: InlineTextInterface[] }[],
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

    }
}
</style>