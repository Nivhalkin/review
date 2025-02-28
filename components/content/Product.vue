<template>
    <article class="product">
        <header class="product-header">
            <div>
                <h3 class="product-header__title">
                    {{ index }}.{{ title }}
                </h3>
                <div class="product-header__author">
                    {{ subTitle }}
                </div>
            </div>
            <figure v-if="badgeIcon">
                <nuxt-img format="webp" :src="`/images/badge-icon.png`" width="115px" height="115px"
                    :alt="`award yellow badge`" />
            </figure>
        </header>
        <section class="product-content">
            <figure>
                <nuxt-img format="webp" class="product-content__img" :src="`/images/${image}`"
                    :alt="`number ${1} top bug product`" width="227" height="333" />
            </figure>
            <div class="product-content-list">
                <ul v-if="prosList" class="product-content-list-pros">
                    <li>
                        PROS
                    </li>
                    <ContentIconLine v-for="(proItemDescription, index) in prosList" :key="`pro--${index}`"
                        :description="proItemDescription" :image="'checked-green-icon.png'" />
                </ul>

                <ul v-if="consList" class="product-content-list-cons">
                    <li>
                        CONS
                    </li>
                    <ContentIconLine v-for="(conItemDescription, index) in consList" :key="`pro--${index}`"
                        :description="conItemDescription" :image="'stop-red-icon.png'" />
                </ul>
            </div>
            <div class="product-content-third">
                <div class="product-content-rating">
                    <h4 class="product-content-rating__title">
                        Rating
                    </h4>
                    <span class="product-content-rating__value">
                        {{ ratingValue }}
                    </span>
                </div>
                <div class="product-content-stars">
                    <figure v-for="index in reviewIconFull" :key="`filled-star-icon--${index}`">
                        <nuxt-img format="webp" :src="`/images/star-icon.png`" width="25px" height="25px"
                            :alt="`yellow star`" />
                    </figure>

                    <figure v-for="index in reviewIconHalf" :key="`filled-star-icon--half${index}`">
                        <nuxt-img format="webp" :src="`/images/star-icon--half.png`" width="25px" height="25px"
                            :alt="`yellow star`" />
                    </figure>
                    <figure v-for="index in reviewIconEmpty" :key="`filled-star-icon--empty${index}`">
                        <nuxt-img format="webp" :src="`/images/star-icon--empty.png`" width="25px" height="25px"
                            :alt="`yellow star`" />
                    </figure>
                    <span class="product-content-stars__number">
                        {{ reviewText }}
                    </span>
                </div>

                <a :id="`${title}--discount`" v-if="ratingLink || learnMore" :href="formattedLinkUrl"
                    class="product-content-link" target="_blank">
                    {{ discountNumber }}
                    <figure class="product-content-link-img" v-if="discountNumber">
                        <nuxt-img format="webp" :src="`/images/badge-discount-icon.png`" width="34px" height="34px"
                            :alt="`discount`" />
                    </figure>
                    {{ buttonRatingText }}
                </a>
            </div>
            <div class="product-content-link--mobile">
                <a :id="title" v-if="ratingLink || learnMore" :href="formattedLinkUrl"
                    class="product-content-link--mobile__value" target="_blank">
                    {{ discountNumber }}
                    <figure class="product-content-link-img">
                        <nuxt-img format="webp" :src="`/images/badge-discount-icon.png`" width="30px" height="30px"
                            :alt="`discount`" />
                    </figure>
                    {{ buttonRatingText }}
                </a>
            </div>

        </section>

        <footer class="product-footer">
            <h3 class="product-footer__title">
                BOTTOM LINE
            </h3>
            <p class="product-footer__description" v-for="(description, index) in bottomLineDescription"
                :key="`product-footer__description--${index}`">
                {{ description }}
            </p>
            <p class="product-footer__description--last">
                *This assessment is based on customer reviews and personal experiences. For more details, please visit the
                product websites.
            </p>

            <div class="product-footer-link">
                <ContentLinkPopup v-if="linkHeadline" class="product-footer-link__popup"
                    text="Over 970+ people chose this site today" />
                <a :id="`${title}--mobile`" class="product-footer__link" :href="formattedLinkUrl" target="_blank">
                    {{ discountNumber ? buttonPurchaseText : 'Click To Shop Now' }}
                </a>
            </div>

        </footer>
    </article>
</template>

<script setup lang="ts">

const route = useRoute()

const { reviewNumber, shopLink, ratingLink } = defineProps<
    {
        title: string;
        subTitle: string;
        badgeIcon: boolean;
        image: string;
        prosList: string[];
        consList: string[];
        reviewNumber: number;
        reviewText: string;
        ratingValue: string;
        ratingLink: string;
        discountNumber?: number;
        bottomLineDescription: string[];
        shopLink: string;
        linkHeadline?: boolean;
        index: number,
        buttonRatingText: string;
        buttonPurchaseText: string;
        learnMore?: boolean
    }>();

const { gclid, fbclid } = route.query

const formattedLinkUrl = (() => {
    if (shopLink?.includes('go.echoique.com')) return shopLink
    if (ratingLink?.includes('go.echoique.com')) return ratingLink
    if (shopLink) {
        if (gclid) return `${shopLink}&utm_medium=392109&gclid=${gclid}`
        else if (fbclid) return `${shopLink}&utm_medium=392109&fbclid=${fbclid}`
        else return `${shopLink}&utm_medium=392109`
    }
    else if (ratingLink) {
        if (gclid) return `${ratingLink}&utm_medium=392109&gclid=${gclid}`
        else if (fbclid) return `${ratingLink}&utm_medium=392109&fbclid=${fbclid}`
        else return `${ratingLink}&utm_medium=392109`
    }
    return ''
})()

const reviewIconFull = Math.floor(reviewNumber)

const reviewIconHalf = reviewNumber.toString().length === 3 ? 1 : 0
const reviewIconEmpty = 5 - Math.round(reviewNumber)

</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.product {
    border: 1px solid var(--product-border-color);
    padding: 16px 45px 30px 45px;
    border-radius: 6px;

    &-header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 23px;

        &__title {
            font-size: 28px;
            font-style: normal;
            font-weight: 800;
            margin-bottom: 2px;
        }

        &__author {
            font-size: 16px;
            font-weight: 300;
        }
    }

    &-content {
        display: flex;
        border-top: 1px solid var(--product-content-border-color);
        border-bottom: 1px solid var(--product-content-border-color);
        margin-bottom: 22px;

        :nth-child(2) {
            flex: 3;
        }

        >* {
            flex: 2;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        &-list {
            display: block;
            padding: 22px 20px;
            border-left: 1px solid var(--product-content-border-color);
            border-right: 1px solid var(--product-content-border-color);

            &-pros {
                color: $section-sucess-color;
                margin-bottom: 13px;
                display: flex;
                flex-direction: column;
                gap: 5px;

                >:first-child {
                    font-size: 28px;
                    font-weight: 700;
                    display: block;
                    margin-bottom: 15px;
                }
            }

            &-cons {
                color: $section-failure-color;
                display: flex;
                flex-direction: column;
                gap: 5px;

                > :first-child {
                    font-size: 28px;
                    font-weight: 700;
                    display: block;
                    margin-bottom: 15px;
                }
            }
        }

        &-third {
            align-self: center;
            display: flex;
            flex-direction: column;
            padding-left: 20px;
        }


        &-rating {
            padding: 22px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            background: $product-content-rating-background-color;
            border-radius: 6px;
            width: 250px;
            height: 250px;
            margin-bottom: 20px;

            &__title {
                font-size: 25px;
                font-weight: 600;
                padding-top: 20px;
            }

            &__value {
                font-size: 150px;
                font-weight: 600;
            }

        }

        &-stars {
            display: flex;
            align-items: center;
            gap: 5px;
            margin-bottom: 23px;

            &__number {
                display: inline-flex;
                margin-left: 10px;
                font-size: 15px;
                font-weight: 400;
            }
        }

        &-link {
            background: var(--product-content-rating-background-color);
            color: var(--product-content-rating-text-color);
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: var(--product-content-rounded);
            padding: 0.5vw 2vw;
            font-size: 23px;
            font-weight: 700;
            transition: background .3s ease;

            &-learn-more {
                background: #000;
                color: white;
                border-radius: 5px;
                width: 100%;
                text-align: center;
                padding: 10px 0;
                margin-bottom: 20px !important;
                transition: background .3s ease;
                max-width: 250px;

                &:hover {
                    background: #4c4c4c;
                }
            }

            &--mobile {
                display: none;
            }

            &:hover {
                background: #c53d07;
            }

            &-img {
                margin: 0 5px;
                display: flex;
            }
        }
    }

    &-footer {

        &__title {
            font-size: 28px;
            font-weight: 800;
            margin-bottom: 23px;
        }

        &__description {
            font-size: 18px;
            margin-bottom: 20px;

            &--last {
                font-size: 14px;
                margin-bottom: 30px;
            }
        }

        &-link {
            display: flex;
            justify-content: center;
            flex-direction: column;
            align-items: center;

            &__popup {
                margin-bottom: 12px;
            }
        }

        &__link {
            border-radius: var(--product-content-rounded);
            background: var(--product-content-purchase-background-color);
            text-align: center;
            padding: 18px 105px;
            color: var(--product-content-purchase-text-color);
            font-size: 25px;
            font-weight: 700;
            transition: background .3s ease;

            &:hover {
                background: #0a1f48;
                cursor: pointer;
            }

            &--alt {
                border-radius: 6px;
                background: #FBBE20;

                &:hover {
                    background: #D8A31D;
                }
            }


        }
    }

    @media (max-width: 1024px) {
        padding: 20px;

        &-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 23px;

            &__title {
                font-size: 20px;
            }

            &__author {
                font-size: 12px;
            }

            figure img {
                width: 63px;
                height: 63px;
                margin-right: 30px;
            }
        }

        &-content {
            flex-wrap: wrap;
            margin-bottom: 20px;

            >figure {
                border-right: 1px solid var(--product-content-border-color);
                padding: 5px;
            }

            >figure img {
                height: auto;
                width: 100%;
                max-width: 250px;
                min-width: 100px;
                aspect-ratio: auto 227 / 333;
            }

            &-third {
                align-self: stretch;
                order: 2;
                width: 100%;
                padding-left: 13px;
            }

            &-list {

                &-pros,
                &-cons {


                    >span {
                        font-size: 20px;
                    }
                }

                order: 4;
                width: 100%;
                flex: auto !important;
                border: none;
            }

            &-rating {
                width: 100%;
                padding: 13px;
                margin-top: 26px;
                max-width: 32vw;
                height: 30vw;

                &__title {
                    font-size: 14px;
                }

                &__value {
                    font-size: 100px;
                    line-height: 90px;
                    flex: initial !important;
                }
            }

            &-link {
                display: none;

                &--mobile {
                    display: block;
                    order: 3;
                    min-width: 80vw;
                    border-top: 1px solid var(--product-content-border-color);

                    &__value {
                        background: $product-content-link-background-color;
                        color: #FFF;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                        border-radius: var(--product-content-rounded);
                        padding: 12px 40px;
                        font-size: 15px;
                        font-weight: 700;
                        margin: 20px 0 !important;

                        >figure img {
                            width: 20px;
                            height: 20px;
                            margin-top: 3px;
                        }
                    }

                }
            }

            &-stars {
                gap: 3px;
                margin-bottom: 21px !important;

                figure img {
                    width: 15px;
                    height: 15px;
                }

                &__number {
                    font-size: 12px;
                    margin-left: 6px;
                }
            }
        }

        &-footer {
            &__title {
                font-size: 20px;
                margin-bottom: 20px;
            }

            &__description {
                font-size: 12px;

                &--last {
                    font-size: 9px;
                }
            }

            &__link {
                font-size: 14px;
                padding: 12px 43px;
            }
        }
    }

    @media (max-width: 500px) {
        &-content {
            &-stars {
                gap: 3px;
                margin-bottom: 21px !important;

                figure img {
                    width: 10px;
                    height: 10px;
                }

                &__number {
                    font-size: 10px;
                    margin-left: 3px;
                }
            }

            &-link-learn-more {
                font-size: 14px;
            }

            &-rating {

                &__title {
                    font-size: 12px;
                    padding-top: 0px;
                }

                &__value {
                    font-size: 60px;
                    line-height: 60px;
                }
            }
        }
    }
}
</style>