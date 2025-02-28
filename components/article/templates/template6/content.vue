<template>
    <main class="content" :style="{
        '--background-color': article.layout.contentBackgroundColor
    }">
        <ArticleTemplatesTemplate6Header id="header-test" :style="{
            '--header-background': article.layout.headerBackgroundColor
        }" :title="article.title" />
        <div class="content-container">
            <ArticleTemplatesTemplate6Introduction :style="{
                '--introduction-background-color': article.introduction.backgroundColor
            }" class="content-section content-section-1" :avatar="article.introduction.avatar"
                :writtenBy="article.introduction.writtenBy" :date="article.introduction.date" :title="article.introduction.title"
                :descriptions="article.introduction.descriptions" />
            <section>
                <div id="scroll-1">
                    <div class="products content-section-5">
                        <ArticleTemplatesTemplate6Product class="products-item" v-for="product in  article.products"
                            :key="product.toString()" :style="{
                                '--product-border-color': product.borderColor,
                                '--product-button-background-color': product.button.backgroundColor,
                                '--product-button-text-color': product.button.textColor,
                                '--product-button-border-radius':
                                    product.button.rounded ? (product.button.isXl ? '60px' : '30px') : '6px'
                                ,
                                '--product-button-border-color': product.button.borderColor,
                                '--circular-inner-color': product.ranking.backgroundInnerColor,
                                '--circular-filled-color': product.ranking.backgroundFilledColor
                            }" :title="product.title" :subTitle="product.subTitle" :badgeIcon="product.badgeIcon"
                            :image="product.image" :ranking="product.ranking" :prosList="product.prosList"
                            :consList="product.consList" :button="product.button" />
                    </div>
                </div>
                <div class="content-best-choice">
                    <ArticleTemplatesTemplate6BestChoice :style="{
                        '--best-choice-header-background-color': article.bestChoice.layout.headerBackgroundColor,
                        '--best-choice-background-color': article.bestChoice.layout.backgroundColor,
                        '--best-choice-border-color': article.bestChoice.layout.borderColor,
                        '--best-choice-border-radius': article.bestChoice.layout.rounded ? '6px' : '0',
                        '--best-choice-button-background-color': article.bestChoice.button.backgroundColor,
                        '--best-choice-button-text-color': article.bestChoice.button.textColor,
                        '--best-choice-button-border-radius': article.bestChoice.button.rounded ? '30px' : '6px',
                        '--best-choice-footer-background-color': article.bestChoice.layout.footerBackgroundColor
                    }" :headerTitle="article.bestChoice.headerTitle" :title="article.bestChoice.title"
                        :image="article.bestChoice.image" :list="article.bestChoice.list"
                        :description="article.bestChoice.description" :button="article.bestChoice.button"
                        :footer="article.bestChoice.footer" />
                </div>
                <div class="evaluated-container-test">
                    <div class="evaluated-container">
                        <ArticleTemplatesTemplate6Evaluated class="content-section-4 evaluated-container-section1" :style="{
                        }" :title="article.evaluated.title" :list="article.evaluated.list" />
                        <h3 class="evaluated-container__title">
                            <CommunInlineText v-for="item in article.evaluated.title2" :key="item.toString()"
                                :text="item.text" :isBold="item.isBold" :textColor="item.textColor"
                                :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined" :link="item.link" />
                        </h3>
                        <section class="evaluated-container-info">
                            <div class="evaluated-container-info-item" v-for="info in article.evaluated.informationList"
                                :key="info.text.toString()" :style="{
                                    '--linear-filled-color': info.bar.color
                                }">
                                <p class="evaluated-container-info-item__text">
                                    <CommunInlineText v-for="item in info.text" :key="item.text" :text="item.text"
                                        :isBold="item.isBold" :textColor="item.textColor"
                                        :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                                        :link="item.link" />
                                </p>
                                <div class="evaluated-container-info-item-grade">
                                    <CommunLineProgressBar :percentage="info.bar.value * 10">
                                        <span class="evaluated-container-info-item-grade__inner">
                                            {{ info.bar.value }} AVG.
                                        </span>
                                    </CommunLineProgressBar>
                                    <p class="evaluated-container-info-item-grade__text">
                                        {{ info.bar.value }}/10
                                    </p>
                                </div>
                            </div>
                        </section>
                        <p class="evaluated-container__paragraph" v-for="item in article.evaluated.description"
                            :key="item.toString()">
                            <CommunInlineText v-for="description in item.paragraph" :key="description.text"
                                :text="description.text" :isBold="description.isBold" :textColor="description.textColor"
                                :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                                :link="description.link" />
                        </p>
                        <div class="evaluated-container-button-content">
                            <NuxtLink :class="`evaluated-container-button evaluated-container-button--xl`"
                                to="https://go.echoique.com/click/1">
                                VISITE WEBSITE >>
                            </NuxtLink>
                        </div>
                    </div>
                </div>
                <ArticleTemplatesTemplate6Sources :title="article.sources.title" :items="article.sources.items" />

            </section>
        </div>
    </main>
</template>

<script setup lang="ts">
const { article } = defineProps<{ article: any }>()

onMounted(() => {
    if (article.script.length > 0) {
        const script = document.createElement('script')
        script.src = article.script
        script.defer = true
        document.body.appendChild(script)
    }
})

</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';


.evaluated-container {
    margin-bottom: 36px;
    padding: 36px 60px;
    background-color: white;
    // border: 4px solid var(--best-choice-border-color);
    filter: drop-shadow(0px 4px 4px #CCD3CB);
    border-radius: 6px;
    width: 100%;

    &-section1 {
        margin-bottom: 86px;
    }


    &__title {
        text-align: center;
        margin-bottom: 36px;
        font-weight: 700;
        font-size: var(--title-font-size);
    }

    &-info {
        padding: 25px 33px 23px 24px;
        background: white;
        border-radius: 10px;
        box-shadow: 0px 4px 4px 2px rgba(205, 212, 203, 0.45);
        margin-bottom: 36px;

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

    &__paragraph {
        font-size: var(--paragraph-font-size);
        margin-bottom: 20px;
    }

    &-button {
        &-content {
            display: flex;
            justify-content: center;
            margin-top: 29px;
        }

        transition: background .2s ease;

        &:hover {
            background: #0F5831;
        }

        margin-bottom: 20px;

        background: #2d9538;
        color: white;
        box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
        text-align: center;
        font-size: 25px;
        font-weight: 700;

        &--xl {
            padding: 15px 74px;
            border-radius: 30px;
        }

    }

    @media (max-width: 1024px) {
        padding: 26px 18px;
        margin-bottom: 26px;

        &-button {
            font-size: 15px;

            &-content {
                justify-content: center;
                margin-top: 26px;
            }
        }

        &-test {
            padding: 0 5px;
        }

        &-section1 {
            margin-bottom: 26px !important;
        }

        &__title {
            margin-bottom: -15px !important;
        }

        &-info {
            padding: 32px 0px;
            margin-bottom: 15px;
            box-shadow: none;

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
    }
}

.products {
    background: #FEFEFE;
    padding: 25px 19px;

    &-item {
        margin-bottom: 36px;

        &:last-child {
            margin-bottom: 0;
        }
    }

    @media (max-width: 1024px) {
        padding: 0px 5px;

        &__title {
            margin-bottom: 71px;
        }

        &-item {
            margin-bottom: 26px;
        }
    }
}

.content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    max-width: 100vw;
    background: var(--background-color);
    --title-font-size: 36px;
    --paragraph-font-size: 16px;
    --title-margin-bottom: 36px;
    padding-bottom: 40px;

    &-container {
        max-width: $breakpoint-max-width--desktop;
        width: 75vw;
    }

    &-back {
        font-size: 20px;
        margin: auto;
        display: flex;
        text-decoration: underline;
        background: transparent;
    }

    &-section {
        filter: drop-shadow(0px 4px 4px #CCD3CB);

        &-1 {
            margin-top: -113px;
            margin-bottom: 36px;
        }

        &-2 {
            margin-bottom: 36px;
        }

        &-3 {
            margin-bottom: 62px;
        }

        &-4 {
            margin-bottom: 86px;
        }

        &-5 {
            margin-bottom: 42px;
        }
    }

    &-best-choice {
        max-width: 54vw;
        display: flex;
        justify-content: center;
        margin: auto;
        margin-bottom: 40px;
    }

    @media (max-width: 1024px) {
        padding-bottom: 27px;

        --title-font-size: 22px;
        --paragraph-font-size: 15px;
        --title-margin-bottom: 16px;

        &-section {
            &-1 {
                margin-top: 0;
                margin-bottom: 58px;
            }

            &-2 {
                margin-bottom: 20px;
            }

            &-3 {
                margin-bottom: 20px;
            }

            &-4 {
                margin-bottom: 71px;
            }

            &-5 {
                margin-bottom: 4px;
            }
        }

        &-container {
            max-width: inherit;
            width: inherit;
            padding: 0;
        }

        &-best-choice {
            max-width: inherit;
            padding: 0px 5px;
            margin-bottom: 49px;
        }
    }
}
</style>