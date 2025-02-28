<template>
    <section class="product">
        <nuxt-img v-if="badgeIcon" loading="lazy" :preload="title[0].text.includes('1')" class="product-badge" format="webp"
            src="/images/icons/badge.svg" alt="badge" />
        <h4 class="product__title">
            <CommunInlineText v-for="item in title" :key="item.text" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </h4>
        <p class="product__subTitle">
            <CommunInlineText v-for="item in subTitle" :key="item.text" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </p>

        <div class="product-content">
            <div class="product-section">
                <div class="product-section__item">
                    <div class="product-section-container">
                        <NuxtLink :to="button.linkUrl" class="product-image">
                            <figure class="product-image-container">
                                <nuxt-img loading="lazy" preload width="434" height="413"
                                    :placeholder="img(`/images/article/${image}`, { h: 10, f: 'png', blur: 2, q: 50 })"
                                    class="product-image__img" alt="product image" :src="`/images/article/${image}`" />
                            </figure>
                        </NuxtLink>
                        <div class="product-button-content product-button--image">
                            <NuxtLink :class="`product-button product-button--${button.isXl ? 'xl' : 'm'}`"
                                :to="button.linkUrl">
                                {{ button.text }}
                            </NuxtLink>
                        </div>
                    </div>

                </div>
                <div class="product-section__item product-section__item--pro-cons">
                    <section class="product-description">
                        <section class="product-description-first-section">
                            <div class="product-description-first-section-list">
                                <ul>
                                    <li class="product-description-first-section-list__item" v-for="itemList in prosList"
                                        :key="itemList.toString()">
                                        <span class="product-description-first-section-list__item__icon">
                                            <IconsChecked1 currentColor="#5FCE92" />
                                        </span>
                                        <CommunInlineText v-for="item in itemList.paragraph" :key="item.toString()"
                                            :text="item.text" :isBold="item.isBold" :textColor="item.textColor"
                                            :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                                            :link="item.link" />
                                    </li>
                                    <li class="product-description-first-section-list__item" v-for="itemList in consList"
                                        :key="itemList.toString()">
                                        <span class="product-description-first-section-list__item__icon">
                                            <IconsCross currentColor="#FF9171" />
                                        </span>
                                        <CommunInlineText v-for="item in itemList.paragraph" :key="item.toString()"
                                            :text="item.text" :isBold="item.isBold" :textColor="item.textColor"
                                            :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                                            :link="item.link" />
                                    </li>
                                </ul>
                            </div>
                            <div class="product-button-content product-button--pros">
                                <NuxtLink :class="`product-button product-button--${button.isXl ? 'xl' : 'm'}`"
                                    :to="button.linkUrl">
                                    {{ button.text }}
                                </NuxtLink>
                            </div>
                        </section>
                    </section>
                </div>
                <div class="product-section__item">
                    <section class="product-ranking">
                        <CommunCircleProgressBar class="product-ranking__circle" :percentage="ranking.value * 10">
                            <section>
                                <div class="product-ranking-circle__value">
                                    {{ ranking.value }}/10
                                </div>
                                <div class="product-ranking-circle__votes">
                                    {{ ranking.votes }} Votes
                                </div>
                            </section>
                        </CommunCircleProgressBar>
                        <p class="product-ranking__text">
                            {{ ranking.text }}
                        </p>
                    </section>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import InlineTextInterface from "~/types/InlineTextInterface";
const img = useImage()

defineProps<{
    image: string,
    title: InlineTextInterface[],
    subTitle: InlineTextInterface[],
    badgeIcon: boolean,
    ranking: {
        value: number,
        votes: string,
        text: string,
    }
    prosList: { paragraph: InlineTextInterface[] }[],
    consList: { paragraph: InlineTextInterface[] }[],
    button: {
        rounded: boolean,
        isXl: boolean,
        backgroundColor: string,
        borderColor: string,
        textColor: string,
        text: string,
        linkUrl: string
    }
}>()
</script>

<style scoped lang="scss">
.product {
    position: relative;
    border: 3px solid var(--product-border-color);
    border-radius: 6px;
    padding: 32px 53px;

    &-badge {
        position: absolute;
        right: 40px;
        top: -25px;
        width: 250px;
    }

    &__title {
        margin-bottom: 5px;
        font-weight: 600;
        font-size: var(--title-font-size);
        text-align: center;
    }

    &__subTitle {
        text-align: center;
        font-size: 20px;
        margin-bottom: 6px;
    }

    &-section {
        display: flex;
        gap: 10px;
        justify-content: space-around;

        &__item {
            padding: 39px 17px;
            width: 21vw;
            background: white;
            border-radius: 10px;
            box-shadow: 0px 4px 4px 2px rgba(205, 212, 203, 0.45);
        }
    }

    &-image {
        overflow: hidden;
        display: block;
        width: 100%;
        height: 100%;
        margin-bottom: 48px;

        &-container {
            width: 100%;
            height: 100%;
        }

        &__img {
            aspect-ratio: auto 434 / 413;
            height: auto;
            width: 100%;
            object-fit: contain;
        }
    }

    &-ranking {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
        flex-direction: column;

        &__circle {
            margin-bottom: 27px;
        }

        &-circle {
            &__value {
                font-size: 2vw;
                font-weight: 600;
                color: var(--circular-filled-color);
                letter-spacing: -1px;
            }

            &__votes {
                font-size: 1vw;
                font-weight: 600;
            }
        }

        &__text {
            font-size: 20px;
            font-weight: 600;
        }
    }

    &-description {
        display: flex;
        width: 100%;

        &-first-section {

            &-list {

                &__item {
                    font-size: var(--paragraph-font-size);
                    font-style: normal;
                    margin-bottom: 8px;
                    display: flex;
                    align-items: center;

                    &__icon {
                        margin-right: 5px;
                    }

                    &:last-child {
                        margin-bottom: 0px;
                    }
                }
            }
        }
    }

    &-button {
        background: var(--product-button-background-color);
        color: var(--product-button-text-color);
        box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
        text-align: center;
        border: 1px solid var(--product-button-border-color);
        font-size: 22px;
        font-weight: 700;
        width: 100%;

        transition: background .2s ease;

        &:hover {
            background: #0F5831;
        }

        &--pros {
            display: none !important;
        }

        &--xl {
            padding: 12px 0px;
            border-radius: var(--product-button-border-radius);
        }

        &--m {
            padding: 16px 90px;
            border-radius: var(--product-button-border-radius);
        }

        &-content {
            display: flex;
            justify-content: center;
        }
    }

    @media (max-width: 1024px) {
        padding: 36px 12px;

        &-badge {
            position: absolute;
            right: 50%;
            transform: translate3d(50%, 0, 0);
            top: -38px;
            width: 125px;
        }

        &__subTitle {
            font-size: 18px;
            margin-bottom: 10px;
        }

        &-section {
            flex-wrap: wrap;
            justify-content: space-between;

            &-container {
                width: 100%;
                height: 100%;
            }

            &__item {
                padding: 10px;
                min-height: 140px;
                height: 35vw;
                width: 48%;
            }

            &__item--pro-cons {
                min-width: 60vw;
                width: 100%;
                min-height: inherit;
                order: 3;
                width: 100%;
                height: inherit;
            }
        }

        &-image {
            padding: 0;
            height: 100%;
            text-align: center;
            margin-bottom: 0;

            &__img {
                height: 100%;
                width: inherit;
            }
        }

        &-ranking {
            &__circle {
                margin-bottom: 5px;
            }

            &-circle {
                &__value {
                    font-size: 20px;
                    margin-bottom: 2px;
                }

                &__votes {
                    font-size: 12px;
                    width: 120%;
                }
            }

            &__text {
                font-size: 12px;
            }
        }

        &-description {
            flex-direction: column;

            &-first-section {
                margin-right: 0px;
            }
        }

        &-button {

            &--image {
                display: none !important;
            }

            &--pros {
                display: flex !important;
                max-width: 230px;
                margin: 36px auto;
            }


            font-size: 15px;

            &--xl {
                padding: 16px 24px;
                border-radius: var(--product-button-border-radius);
            }

            &--m {
                padding: 16px 20px;
                border-radius: var(--product-button-border-radius);
            }

            &-content {
                display: flex;
                justify-content: center;
            }
        }
    }
}
</style>