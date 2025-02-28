<template>
    <div :class="`floating-card ${displayCard ? 'floating-card--display' : ''}`">
        <figure class="floating-card__img-container">
            <nuxt-img format="webp" alt="product" :src="`/images/article/${image}`" width="85px" height="90px" />
        </figure>
        <div class="floating-card__content">
            <p>
                <CommunInlineText v-for="item in title" :key="item.text" :text="item.text" :isBold="item.isBold"
                    :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                    :link="item.link" />
            </p>
            <p>
                <CommunInlineText v-for="item in description" :key="item.text" :text="item.text" :isBold="item.isBold"
                    :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                    :link="item.link" />
            </p>
            <NuxtLink class="floating-card__button" :to="button.link">
                {{ button.text }}
            </NuxtLink>
        </div>
    </div>
</template>

<script setup lang="ts">
import InlineTextInterface from "~/types/InlineTextInterface";

const { productNumber } = defineProps<{ image: string, title: InlineTextInterface[], description: InlineTextInterface[], button: { text: string, link: string }, productNumber: number }>()
const displayCard = ref<boolean>(false)

onMounted(() => {

    const observer = new IntersectionObserver((entries) => {
        for (const entry of entries) {
            if (entry.target.id === `product-${productNumber}`) {
                if (entry.isIntersecting && displayCard.value === true) {
                    displayCard.value = false
                    return
                }
                if (entry.boundingClientRect.y < 0) {
                    displayCard.value = true;
                }
                else {
                    displayCard.value = false;
                }

            }
        }
    });
    observer.observe(document?.getElementById(`product-${productNumber}`) as any)
})
</script>

<style lang="scss" scoped>
.floating-card {
    display: flex;
    z-index: 10;
    background: white;
    align-items: center;
    width: 440px;
    border-radius: 10px;
    box-shadow: 0 0 3px 1px #aaa;
    padding: 1rem 1.5rem;
    position: fixed;
    bottom: 0;
    right: 0;
    margin: 2rem;
    pointer-events: none;
    opacity: 0;
    transition: opacity 250ms ease;

    &__img-container {
        margin-right: 18px;
    }

    &--display {
        pointer-events: initial;
        opacity: 1;
    }

    &__content {
        margin: auto;
    }

    &__button {
        margin: auto;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        background: #5bab4c;
        width: fit-content;
        border-radius: 100px;
        font-size: 17px;
        line-height: 1;
        font-weight: 800;
        padding: 1rem 1.85rem;
        margin-top: 14px;
        box-shadow: 2px 6px 8px rgba(0, 60, 60, .07);
        color: white;
        font-weight: 700;
    }

    @media (max-width: 1024px) {
        margin: 0;
        width: 100vw;
        border-radius: 0;
        ;

        &__img-container {
            margin-right: 0;
        }
    }
}
</style>