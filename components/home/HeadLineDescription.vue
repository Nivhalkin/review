<template>
    <section class="headline-description">
        <h3 class="headline-description__title">Unmasking Online Shopping: Your Guide to
            Informed Purchases
        </h3>
        <p class="headline-description__description">Navigate the world of online shopping with Echoique, your reliable
            compass in the bustling digital marketplace.
            We empower you with in-depth insights, unbiased evaluations, and user reviews, while our rigorous testing
            ensures only the best recommendations. With us, you can always choose with confidence.
        </p>
    </section>
</template>

<style lang="scss" scoped>
.headline-description {
    background: #00301F;
    padding: 32px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
    color: #FFF;

    &__title {
        font-size: 25px;
        font-weight: 800;
        margin-bottom: 30px;
        max-width: 536px;
        text-align: center;
    }

    &__description {
        font-size: 18px;
        font-weight: 300;
        max-width: 632px;
        text-align: center;
    }

    @media (max-width: 1024px) {
        padding: 20px;

        &__title {
            font-size: 16px;
            margin-bottom: 10px;
        }

        &__description {
            font-size: 12px;
        }

    }

}
</style>