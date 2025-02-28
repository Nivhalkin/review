<template>
    <section class="best-choice">
        <header class="best-choice-header">
            <figure class="best-choice-header__img">
                <nuxt-img format="webp" :src="`/images/badge-icon.png`" width="140px" height="140px"
                    :alt="`award yellow badge`" />
            </figure>
            <h2 class="best-choice-header__title">{{ sectionTitle }}</h2>
        </header>
        <div class="best-choice-content">
            <figure class="best-choice-content__logo">
                <nuxt-img format="webp" :src="logo" :alt="`product best choice`" />
            </figure>
            <figure class="best-choice-content__img">
                <nuxt-img format="webp" :src="image" :alt="`product best choice`" />
            </figure>

            <div class="best-choice-content-description">
                <h4 class="best-choice-content-description__title">
                    {{ title }}
                </h4>
                <span class="best-choice-content-description__subtitle">
                    {{ subTitle }}
                </span>
                <ul class="best-choice-content-description-list">
                    <ContentIconLine v-for="text in list" :key="text" :description="text" :showIcon="listIcon"
                        image="checked-green-icon.png" />
                </ul>
            </div>
            <div class="best-choice-content--mobile">
                <div class="best-choice-content-buy-stars">
                    <figure v-for="index in 5" :key="`filled-star-icon--${index}`">
                        <nuxt-img format="webp" :src="`/images/star-icon.png`" width="25px" height="25px"
                            :alt="`yellow star`" />
                    </figure>
                </div>
                <div class="best-choice-content-buy-learn">
                    Learn More
                </div>
                <div class="best-choice-content-buy-txt">
                    {{ reviewText }}
                </div>
                <ContentLinkPopup v-if="showButtonText" class="best-choice-content-buy__link-popup"
                    text="Over 970+ people chose this site today" />
                <a class="best-choice-content-buy__link" :href="formattedLinkUrl" target="_blank">
                    Click To Shop Now
                </a>
            </div>
            <div class="best-choice-content-buy">
                <figure class="best-choice-content-buy__img">
                    <nuxt-img format="webp" :src="logo" :alt="`product company logo`" />
                </figure>
                <div class="best-choice-content-buy-stars">
                    <figure v-for="index in 5" :key="`filled-star-icon--${index}`">
                        <nuxt-img format="webp" :src="`/images/star-icon.png`" width="25px" height="25px"
                            :alt="`yellow star`" />
                    </figure>
                </div>
                <div class="best-choice-content-buy-learn">
                    Learn More
                </div>
                <div class="best-choice-content-buy-txt">
                    {{ reviewText }}
                </div>
                <ContentLinkPopup v-if="showButtonText" class="best-choice-content-buy__link-popup"
                    text="Over 970+ people chose this site today" />
                <a :class="'best-choice-content-buy__link'" :href="formattedLinkUrl" target="_blank">
                    {{ buttonText }}
                </a>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
const route = useRoute()

const { gclid, fbclid } = route.query
const { link } = defineProps<{
    link: string, image: string, listIcon: boolean, showButtonText: boolean, sectionTitle: string, title: string, subTitle: string, list: string[], logo: string, reviewText: string,
    buttonText: string,
}>()

const formattedLinkUrl = (() => {
    if (link.includes('go.echoique.com')) return link
    if (gclid) return `${link}&utm_medium=392109&gclid=${gclid}`
    else if (fbclid) return `${link}&utm_medium=392109&fbclid=${fbclid}`
    else return link
})() 
</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.best-choice {
    border: 3px solid var(--best-choice-border-color);
    border-radius: 6px;

    &-header {
        position: relative;
        background: var(--best-choice-border-color);
        padding: 12px 0;

        &__img {
            position: absolute;
            left: 30px;
        }

        &__title {
            text-align: center;
            color: var(--best-choice-title-color);
            font-size: 27px;
            font-weight: 700;
        }
    }

    &-content {
        padding: 88px 20px 42px 20px;
        display: flex;
        justify-content: space-between;
        align-items: stretch;

        &--mobile {
            display: none;
        }

        &__logo {
            display: none;
        }

        >* {
            flex: 2;
        }

        &:nth-child(2) {
            flex: 3;
        }

        &__img {
            padding-top: 20px;
            margin-bottom: 20px;

            img {
                aspect-ratio: auto 150 / 220;
                height: auto;
                max-height: 400px;
                min-width: 230px;
            }
        }

        &-description {
            display: flex;
            align-items: flex-start;
            justify-content: flex-start;
            flex-direction: column;

            &__title {
                font-size: 28px;
                font-weight: 800;
            }

            &__subtitle {
                font-size: 16px;
                font-weight: 300;
                display: block;
                margin-bottom: 53px;
            }

            &-list {
                list-style: initial;
                display: flex;
                flex-direction: column;
                align-items: center;
                gap: 12px;
                font-size: 20px;
                align-items: flex-start !important;
            }

        }

        &-buy {
            display: flex;
            flex-direction: column;
            align-items: center;

            &__img {
                margin-bottom: 39px;
            }

            &-stars {
                display: flex;
                gap: 5px;
                margin-bottom: 14px;
            }

            &-learn {
                font-size: 20px;
                font-weight: 700;
                margin-bottom: 9px;
            }

            &-txt {
                text-align: center;
                font-size: 17px;
                margin-bottom: 30px;
            }

            &__link-popup {
                margin-bottom: 20px;
            }

            &__link {
                border-radius: var(--best-choice-button-radius);
                background: var(--best-choice-button-background-color);
                text-align: center;
                padding: 18px 30px;
                color: var(--best-choice-button-text-color);
                font-size: 20px;
                font-weight: 700;
                transition: background .3s ease;
                margin-top: auto;

                &:hover {
                    background: #0a1f48;
                }
            }

        }
    }

    @media (max-width: 1024px) {
        &-header {

            &__title {
                font-size: 20px;
                padding: 0 10px;
            }

            &__img {
                bottom: 0;
                left: 10px;
                transform: translate(0, 85%);

                img {
                    width: 100px;
                    height: 100px;
                }
            }
        }

        &-content {
            justify-content: center;
            align-items: center;
            flex-direction: column;

            &-description {

                &__title,
                &__subtitle {
                    display: none;
                }
            }

            &--mobile {
                margin-top: 21px;
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;
            }

            &-buy {
                display: none;

                &-stars {
                    gap: 3px;
                    margin-bottom: 10px;

                    figure img {
                        width: 21px;
                        height: 21px;
                    }
                }

                &-learn {
                    font-size: 15px;
                    margin-bottom: 5px;
                }

                &-txt {
                    font-size: 12px;
                    max-width: 140px;
                    margin-bottom: 20px;
                }

                &__link {
                    font-size: 15px;
                    padding: 15px 30px;
                }
            }

            &__logo {
                display: block;

                img {
                    aspect-ratio: auto 120 / 39;
                    max-width: 150px;
                }
            }

            &__img {
                text-align: center;
                padding-top: 15px;

                img {
                    width: 30vw;
                    min-width: 150px;
                }
            }
        }

    }
}
</style>