<template>
    <section class="product">
        <nuxt-img v-if="badgeIcon" loading="lazy" :preload="title[0].text.includes('1')" class="product-badge"
            format="webp" src="/images/icons/badge.svg" alt="badge" />
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
                <div class="product-section__item product-section__item--grade">
                    <section class="product-rating">
                        <div class="product-rating__value">{{ rating.value }}</div>
                        <p class="product-rating__text">{{ rating.text }}</p>
                    </section>

                </div>
                <div class="product-section__item product-section__item--flex">
                    <NuxtLink :to="button.linkUrl" class="product-image">
                        <figure class="product-image-container">
                            <nuxt-img loading="lazy" preload format="webp"
                                :placeholder="img(`/images/article/${image}`, { h: 10, f: 'png', blur: 2, q: 50 })"
                                class="product-image__img" alt="product image" :src="`/images/article/${image}`"
                                width="300" height="300" />
                        </figure>
                    </NuxtLink>
                </div>
                <div class="product-section__item product-section__item--flex">
                    <section class="product-ranking">
                        <CommunCircleProgressBar class="product-ranking__circle" :percentage="ranking.value * 10">
                            <section>
                                <div class="product-ranking-circle__value">
                                    {{ ranking.value }}/10
                                </div>
                            </section>
                        </CommunCircleProgressBar>
                        <p class="product-ranking__text">
                            {{ ranking.text }}
                        </p>
                    </section>
                </div>
            </div>
            <section class="product-info" v-if="kpiIsDisplayed">
                <div class="product-info-item" v-for="info in informationList" :key="info.text.toString()" :style="{
                    '--linear-filled-color': info.bar.color
                }">
                    <p class="product-info-item__text">
                        <CommunInlineText v-for="item in info.text" :key="item.text" :text="item.text"
                            :isBold="item.isBold" :textColor="item.textColor" :highlightColor="item.highlightColor"
                            :isUnderlined="item.isUnderlined" :link="item.link" />
                    </p>
                    <div class="product-info-item-grade">
                        <CommunLineProgressBar :percentage="info.bar.value * 10">
                            <span class="product-info-item-grade__inner">
                                {{ info.bar.value }} AVG.
                            </span>
                        </CommunLineProgressBar>
                        <p class="product-info-item-grade__text">
                            {{ info.bar.value }}/10
                        </p>
                    </div>
                </div>
            </section>
            <section class="product-description">
                <section class="product-description-first-section">
                    <div class="product-description-first-section-list">
                        <h4 class="product-description-first-section-list__title">
                            Pros
                        </h4>
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
                        </ul>

                    </div>
                    <div class="product-description-first-section-list">
                        <h4 class="product-description-first-section-list__title">
                            Cons
                        </h4>
                        <ul>
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
                </section>
                <section class="product-description-bottom-line">
                    <h4 class="product-description-bottom-line__title">
                        The bottom Line
                    </h4>
                    <p class="product-description-bottom-line__paragraph" v-for="item in bottomLineDescription"
                        :key="item.toString()">
                        <CommunInlineText v-for="description in item.paragraph" :key="description.text"
                            :text="description.text" :isBold="description.isBold" :textColor="description.textColor"
                            :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                            :link="description.link" />
                    </p>
                </section>
            </section>
            <div class="product-button-content">
                <NuxtLink :class="`product-button product-button--${button.isXl ? 'xl' : 'm'}`" :to="button.linkUrl">
                    {{ button.text }}
                </NuxtLink>
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
    rating: {
        text: string,
        value: string
    },
    ranking: {
        value: number,
        votes: string,
        text: string,
    }
    informationList: { text: InlineTextInterface[], bar: { color: string, value: number } }[],
    prosList: { paragraph: InlineTextInterface[] }[],
    consList: { paragraph: InlineTextInterface[] }[],
    bottomLineDescription: { paragraph: InlineTextInterface[] }[],
    button: {
        rounded: boolean,
        isXl: boolean,
        backgroundColor: string,
        borderColor: string,
        textColor: string,
        text: string,
        linkUrl: string
    }
    kpiIsDisplayed: boolean
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
        top: -58px;
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
        margin-bottom: 29px;

        &__item {
            padding: 42px 29px;
            width: 21vw;
            height: 21vw;
            background: white;
            border-radius: 10px;
            box-shadow: 0px 4px 4px 2px rgba(205, 212, 203, 0.45);
        }
    }

    &-rating {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        height: 100%;

        &__value {
            font-size: 10vw;
        }

        &__text {
            font-size: 20px;
            font-weight: 600;
        }
    }

    &-image {
        overflow: hidden;
        display: block;
        width: 100%;
        height: 100%;

        &-container {
            width: 100%;
            height: 100%;
        }

        &__img {
            height: 100%;
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
        }

        &__text {
            font-size: 20px;
            font-weight: 600;
        }
    }

    &-info {
        padding: 25px 33px 23px 24px;
        background: white;
        border-radius: 10px;
        box-shadow: 0px 4px 4px 2px rgba(205, 212, 203, 0.45);
        margin-bottom: 26px;

        &-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 7px;

            &:last-child {
                margin-bottom: 0px;
            }

            &__text {
                flex: 4;
                font-size: 18px;
                font-weight: 600;
            }

            &-grade {
                flex: 6;
                display: flex;
                justify-content: flex-end;
                align-items: center;
                gap: 12px;

                &__inner {
                    font-size: 14px;
                    font-style: normal;
                    font-weight: 500;
                    color: #FFFFFF;
                    width: 100%;
                    text-align: end;
                    display: inline-block;
                    padding-right: 10px;
                }

                &__text {
                    font-size: 14px;
                    font-style: italic;
                    font-weight: 500;
                }
            }
        }
    }

    &-description {
        display: flex;
        width: 100%;
        margin-bottom: 36px;

        &-first-section {
            flex: 2;
            background: white;
            border-radius: 10px;
            box-shadow: 0px 4px 4px 2px rgba(205, 212, 203, 0.45);
            margin-right: 23px;

            &-list {
                padding: 17px;

                &__title {
                    font-size: 21px;
                    font-weight: 600;
                    margin-bottom: 16px;
                }

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

        &-bottom-line {
            padding: 19px 30px 36px 30px;
            flex: 5;
            background: white;
            border-radius: 10px;
            box-shadow: 0px 4px 4px 2px rgba(205, 212, 203, 0.45);

            &__title {
                font-size: 21px;
                font-weight: 600;
                margin-bottom: 16px;
            }

            &__paragraph {
                font-size: var(--paragraph-font-size);
                margin-bottom: 20px;
            }

            &__asterix {
                font-size: 12px;
                margin-top: auto;
            }
        }
    }

    &-button {
        background: var(--product-button-background-color);
        color: var(--product-button-text-color);
        box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
        text-align: center;
        border: 4px solid var(--product-button-border-color);
        font-size: 25px;
        font-weight: 700;

        transition: color .3s ease;

        &:hover {
            color: black;
        }

        &--xl {
            padding: 25px 70px;
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
        padding: 38px 12px;

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
            margin-bottom: 15px;

            &__item {
                padding: 10px;
                min-width: 140px;
                min-height: 140px;
                height: 35vw;
                width: 35vw;

                &--flex {
                    flex: 1;
                }
            }

            &__item--grade {
                order: 3;
                min-width: 60vw;
                height: 64px;
                width: 100%;
                min-height: inherit;
            }
        }

        &-image {
            padding: 0;
            height: 100%;
            text-align: center;

            &__img {
                height: 100%;
                width: inherit;
            }
        }

        &-rating {
            flex-direction: row;

            &__value {
                font-size: 30px;
                font-weight: 700;
                margin-right: 20px;
            }

            &__text {
                font-size: 12px;
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

        &-info {
            padding: 32px 17px;
            margin-bottom: 15px;

            &-item {
                align-items: flex-start;
                flex-direction: column;
                margin-bottom: 4px;

                &__text {
                    flex: 1;
                    font-size: 15px;
                    margin-bottom: 2px;
                }

                &-grade {
                    flex: 1;
                    width: 100%;

                    &__inner,
                    &__text {
                        font-size: 13px;
                    }
                }
            }
        }

        &-description {
            flex-direction: column;
            margin-bottom: 36px;

            &-first-section {
                margin-bottom: 11px;
                margin-right: 0px;
            }
        }

        &-button {
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