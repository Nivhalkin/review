<template>
    <button @click="scrollToTop5()" :class="`floating-button ${isNavigationDisplayed ? 'floating-button--display' : ''}`">
        {{ text }}</button>
</template>

<script setup lang="ts">
const { elementRef } = defineProps<{ text: string, elementRef: string }>()
const isIntersectingIntroduction = ref<boolean>(true)
const isIntersectingProduct = ref<boolean>(false)

const scrollToTop5 = () => {
    scrollTop5Element.value?.scrollIntoView({ behavior: 'smooth', })
}
const isNavigationDisplayed = computed(() => {
    return !isIntersectingProduct.value && !isIntersectingIntroduction.value
})

const scrollTop5Element = ref<HTMLElement | null>(null);
onMounted(() => {
    scrollTop5Element.value = document?.getElementById(elementRef)

    const observer = new IntersectionObserver((entries) => {

        for (const entry of entries) {
            if (entry.target.id === "header-test") {
                if (entry.isIntersecting) {
                    isIntersectingIntroduction.value = true
                } else {
                    isIntersectingIntroduction.value = false
                }
            }

            if (entry.target.id === "scroll-1") {
                if (entry.isIntersecting) {
                    isIntersectingProduct.value = true
                }
                else {
                    isIntersectingProduct.value = false
                }
            }
        }
    });
    observer.observe(document?.getElementById('header-test') as any)
    observer.observe(scrollTop5Element.value as any)
})
</script>

<style lang="scss" scoped>
.floating-button {
    position: fixed;
    right: 50px;
    bottom: 100px;
    padding: 25px 36px;
    background: var(--floating-button-background-color);
    color: var(--floating-button-text-color);
    border-radius: 40px;
    z-index: 1;
    font-size: 17px;
    font-weight: 700;
    transition: .2s opacity ease;
    opacity: 0;
    pointer-events: none;
    border: 5px solid var(--floating-button-border-color);

    &--display {
        pointer-events: initial;
        opacity: 1;
    }

    @media (max-width: 1024px) {
        font-size: 15px;
        padding: 17px 31px;
        right: 10px;
        bottom: 40px;
    }
}
</style>