<template>
    <main class="content">
        <div class="content-container">
            <section>
                <ContentHeader class="content-header" :title="article.header.title"
                    :description="article.header.description" />
                <ContentHeaderNavigation :navigation="article.header.navigation" />
                <CommunImageDescription :image="article.header.image" :descriptions="article.header.imageDescriptions" />
                <ContentTitleDescription id="scroll-2" :title="article.sectionTitleDescriptions.title"
                    :descriptions="article.sectionTitleDescriptions.descriptions" />
                <ContentBenefits v-bind="article.benefits" class="content-benefits" :style="{
                    '--benefits-title-color': article.benefits.titleColor,
                    '--benefits-header-color': article.benefits.headerBackgroundColor
                }" />
                <ContentWhyYouNeedIt :title="article.keyConsideration.title"
                    :descriptions="article.keyConsideration.descriptions" :lookfor="article.lookFor" :avoid="article.avoid"
                    class="content-why" />
                <ContentProducts :style="{
                    '--product-border-color': article.products.borderColor,
                    '--product-content-border-color': article.products.contentBorderColor,
                    '--product-content-rounded': article.products.buttons.rounded ? '60px' : '6px',
                    '--product-content-rating-text-color': article.products.buttons.rating.textColor,
                    '--product-content-rating-background-color': article.products.buttons.rating.backgroundColor,
                    '--product-content-purchase-background-color': article.products.buttons.purchase.backgroundColor,
                    '--product-content-purchase-text-color': article.products.buttons.purchase.textColor
                }" class="content-products" :products="article.products.items" :title="article.products.title"
                    :buttons="article.products.buttons" :description="article.products.description"
                    :buttonRatingText="article.products.buttons.rating.text"
                    :buttonPurchaseText="article.products.buttons.purchase.text" />
                <ContentBestChoice class="content-best-choice" :style="{
                    '--best-choice-border-color': article.bestChoice.borderColor,
                    '--best-choice-title-color': article.bestChoice.titleColor,
                    '--best-choice-button-radius': article.bestChoice.buttons.rounded ? '60px' : '6px',
                    '--best-choice-button-text-color': article.bestChoice.buttons.textColor,
                    '--best-choice-button-background-color': article.bestChoice.buttons.backgroundColor
                }" :buttonText="article.bestChoice.buttons.text" :sectionTitle="article.bestChoice.sectionTitle"
                    :title="article.bestChoice.title" :sub-title="article.bestChoice.subTitle"
                    :list="article.bestChoice.list" :logo="article.bestChoice.logo"
                    :review-text="article.bestChoice.reviewText" :showButtonText="article.bestChoice.showButtonText"
                    :listIcon="article.bestChoice.listIcon" :image="article.bestChoice.image"
                    :link="article.bestChoice.link" />
                !
                <button class="content-back" @click="scrollToElement()">
                    Back to the Best Option
                </button>
            </section>
        </div>
    </main>
</template>

<script setup lang="ts">
import Template3 from '@/types/Template3Interface';

defineProps<{ article: Template3 }>();

let scrollElementOne: HTMLElement | null;

onMounted(() => {
    scrollElementOne = document?.getElementById('scroll-1')
})

const scrollToElement = (): void => {
    if (scrollElementOne) {
        scrollElementOne.scrollIntoView({ behavior: 'smooth', })
    }
}

</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    max-width: 100vw;

    &-container {
        max-width: $breakpoint-max-width--desktop;
    }

    &-header {
        margin-bottom: 20px;
    }

    &-benefits {
        margin-bottom: 30px;
    }

    &-why {
        margin-bottom: 30px;
    }

    &-products {
        margin-bottom: 50px;
    }

    &-best-choice {
        margin-bottom: 76px;
    }

    &-back {
        font-size: 20px;
        margin: auto;
        display: flex;
        text-decoration: underline;
        background: transparent;
    }

    @media (max-width: 1024px) {
        &-container {
            max-width: inherit;
            padding: 0 20px;
        }

        &-header {
            margin-bottom: 15px;
        }

        &-back {
            font-size: 12px;
        }

    }
}
</style>