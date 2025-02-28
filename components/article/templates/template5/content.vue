<template>
    <main class="content" :style="{
        '--background-color': article.layout.contentBackgroundColor,
        '--max-width': article.layout.contentMaxWidth ?? '70vw'
    }">
        <CommunFloatingCard :image="article.floatingCard.img" :button="article.floatingCard.button"
            :title="article.floatingCard.title" :description="article.floatingCard.description" :product-number="1" />
        <CommunFloatingButton :style="{
            '--floating-button-background-color': article.floatingButton.backgroundColor,
            '--floating-button-text-color': article.floatingButton.textColor,
            '--floating-button-border-color': article.floatingButton.borderColor
        }" :text="article.floatingButton.text" elementRef="scroll-1" />
        <ArticleTemplatesTemplate5Header id="header-test" :style="{
            '--header-background': article.layout.headerBackgroundColor,
            '--header-navigation-border-color': article.header.navigationBorderColor,
            '--header-navigation-border-radius': article.header.navigationBorderIsRounded ? '40px' : '6px'
        }" :title="article.title" :subTitle="article.subTitle" :navigationTitle="article.header.navigationTitle"
            :navigationItems="article.header.navigationItems" />
        <div class="content-container">
            <ArticleTemplatesTemplate5Introduction :style="{
                '--introduction-background-color': article.introduction.backgroundColor
            }" class="content-section content-section-1" :avatar="article.introduction.avatar"
                :writtenBy="article.introduction.writtenBy" :date="article.introduction.date"
                :section1title="article.introduction.section1Title"
                :section1Descriptions="article.introduction.section1Descriptions"
                :section2title="article.introduction.section2Title"
                :section2Descriptions="article.introduction.section2Descriptions"
                :section2List="article.introduction.section2List" />
            <ArticleTemplatesTemplate5Benefits id="scroll-3" class="content-section content-section-2" :style="{
                '--benefits-background-color': article.benefits.backgroundColor,
                '--benefits-list-item-background-color': article.benefits.listItemBackgroundColor,
            }" :section1title="article.benefits.section1Title" :section1subTitle="article.benefits.Section1SubTitle"
                :section2title="article.benefits.section2Title
                    " :section2List="article.benefits.section2List" :iconsColor="article.benefits.iconsColor" />
            <ArticleTemplatesTemplate5Lookfor class="content-section content-section-2" :style="{
                '--lookfor-background-color': article.lookfor.backgroundColor
            }" :title="article.lookfor.title" :description="article.lookfor.description" :list="article.lookfor.list"
                :iconsColor="article.lookfor.iconsColor" />
            <ArticleTemplatesTemplate5CheckList id="scroll-2" class="content-section content-section-3" :style="{
                '--checkList-background-color': article.checkList.backgroundColor,
                '--checkList-list-border-color': article.checkList.borderListColor
            }" :title="article.checkList.title" :description="article.checkList.description"
                :iconsColor="article.checkList.iconsColor" :list="article.checkList.list" />

            <ArticleTemplatesTemplate5Evaluated v-if="article.evaluated.isDisplayed" class="content-section-4" :style="{
            }" :title="article.evaluated.title" :list="article.evaluated.list" />

            <section>
                <div id="scroll-1">

                    <h3 class="products__title">
                        <CommunInlineText v-for="item in article.products.title" :key="item.text" :text="item.text"
                            :isBold="item.isBold" :textColor="item.textColor" :highlightColor="item.highlightColor"
                            :isUnderlined="item.isUnderlined" :link="item.link" />
                    </h3>
                    <div class="products content-section-5">
                        <ArticleTemplatesTemplate5Product :id="`product-${index + 1}`" class="products-item"
                            v-for="(product, index) in article.products.items" :key="product.toString()" :style="{
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
                            :rating="product.rating" :image="product.image" :ranking="product.ranking"
                            :informationList="product.informationList" :prosList="product.prosList"
                            :consList="product.consList" :bottomLineDescription="product.bottomLineDescription"
                            :button="product.button" :kpiIsDisplayed="product.kpiIsDisplayed" />
                    </div>
                </div>
                <div class="content-best-choice">
                    <ArticleTemplatesTemplate5BestChoice :style="{
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
                        :footer="article.bestChoice.footer" :kpiIsDisplayed="article.bestChoice.kpiIsDisplayed" />
                </div>

                <ArticleTemplatesTemplate5Sources :title="article.sources.title" :items="article.sources.items" />

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
        document.body.appendChild(script)
    }
})

</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.products {
    background: #FEFEFE;
    padding: 25px 19px;

    &__title {
        text-align: center;
        margin-bottom: 40px;
        font-weight: 900;
        font-size: var(--title-font-size);
    }

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
        max-width: var(--max-width);
        width: var(--max-width);
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
                margin-bottom: 20px;
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