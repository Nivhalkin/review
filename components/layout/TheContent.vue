<template>
    <main class="content">
        <div class="content-container">
            <section>
                <ContentHeader class="content-header" :title="article.header.title"
                    :description="article.header.description" />
                <ContentHeaderNavigation :navigation="article.header.navigation" />
                <CommunImageDescription :image="article.header.image" :descriptions="article.header.imageDescriptions" />
                <ContentBenefits v-if="!article.isAlt" class="content-benefits" />
                <ContentWhyYouNeedIt v-if="!article.isAlt" class="content-why" />
                <ContentHowItWorks v-if="article.isAlt && !article.alt2 && !article.isOutdoor2" class="content-why" />
                <ContentWhatAre v-if="article.alt2" class="content-why" />
                <ContentWhyYouNeedItAltHealth2 v-if="article.isAlt && article.alt2" class="content-why" />
                <ContentWhyYouNeedItAlt v-if="article.isAlt && !article.alt2 && !article.isOutdoor2" class="content-why" />
                <ContentWhyYouNeedItAltOutdoor v-if="article.isOutdoor2" class="content-why" />
                <ContentProducts class="content-products" :products="article.products.items" :title="article.products.title"
                    :description="article.products.description" :isAlt="article.isAlt" />
                <ContentBestChoice class="content-best-choice" :isAlt="article.isAlt"
                    :sectionTitle="article.bestChoice.sectionTitle" :title="article.bestChoice.title"
                    :sub-title="article.bestChoice.subTitle" :list="article.bestChoice.list" :logo="article.bestChoice.logo"
                    :review-text="article.bestChoice.reviewText" :showButtonText="article.bestChoice.showButtonText"
                    :listIcon="article.bestChoice.listIcon" :image="article.bestChoice.image"
                    :link="article.bestChoice.link" />
                <button class="content-back" @click="scrollToElement()">
                    Back to the Best Option
                </button>
            </section>
        </div>
    </main>
</template>

<script setup lang="ts">
import mainArticles from "../../data/mainArticles"
const route = useRoute()
const category = route.params.name
const id = route.params.id
const article = category === 'health' ? (+id === 6 ? mainArticles().health : mainArticles().health2) : ((route.params.id[1] === '-' && route.params.id[2] === '2') ? mainArticles().outdoor2 : mainArticles().outdoor)

let scrollElementOne: HTMLElement | null;


const shouldAddScript = ref(false);
onMounted(() => {
    scrollElementOne = document?.getElementById('scroll-1')
    if (shouldAddScript.value) {
        const script = document.createElement('script')
        script.src = "https://go.echoique.com/track.js?rtkcmpid=652ea02febd09200018eb98a"
        document.body.appendChild(script)
    }

})

const scrollToElement = (): void => {
    if (scrollElementOne) {
        scrollElementOne.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'nearest' })
    }
}

const inverseArticle = () => {
    if (route.params.id[1] === '-') {
        shouldAddScript.value = true
    }
    if (route.params.id[1] === '-' && route.params.id[2] === '1') {
        const tmpFisrt = article.products.items[0]
        tmpFisrt.prosList = ['Attracts and zaps a broad spectrum of pests', 'Easy to clean and maintain', 'Versatile Hanging Option', 'USB-powered design', 'Suitable for both indoor and outdoor use', 'Good value for money', 'Friendly Return or Replace Policy', 'Instant, effective killing mechanism']
        tmpFisrt.consList = ['Struggles with bigger bugs', 'Battery doesn\'t last long']
        tmpFisrt.linkHeadline = false
        tmpFisrt.ratingValue = 'A'
        tmpFisrt.badgeIcon = false
        tmpFisrt.reviewNumber = 4.5
        tmpFisrt.discountLink = 'https://go.echoique.com/click/2'
        article.bestChoice.link = 'https://go.echoique.com/click/2'
        article.products.items[1].prosList = ['Instantly zaps mosquitoes, flies, and otherbugs on contact', 'Portable, lightweight design for easy indooror outdoor relocation.', 'Lasts 20 hours per charge', 'Attracts bugs up to 20 feet away', 'Easy-clean tray for hassle-free maintenance', 'Safe for kids/pets with shock-preventive grid', 'Chemical-free & odorless', 'Durable, weatherproof design for any climate or conditions.']
        article.products.items[1].consList = ['You need to buy it online.']
        article.products.items[1].linkHeadline = true
        article.products.items[1].ratingValue = 'A+'
        article.products.items[1].badgeIcon = true
        article.products.items[1].reviewNumber = 5
        article.products.items[0] = article.products.items[1]
        article.products.items[1] = tmpFisrt
    }
}

inverseArticle()
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
</style>../../data/mainArticles