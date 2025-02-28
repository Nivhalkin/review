<template>
    <section>
        <h2 id="scroll-3" class="products__title">
            {{ title }}
        </h2>
        <p class="products__headline">
            {{ description }}
        </p>
        <div>

        </div>

        <div class="products-item">
            <ContentProduct v-for="(product, index) in products" :key="`products__item--${product.title}`"
                class="products__item" v-bind="product" :index="index + 1" :buttonRatingText="buttonRatingText"
                :buttonPurchaseText="buttonPurchaseText" />
        </div>

    </section>
</template>

<script setup lang="ts">
import { BugZapperProduct } from "~/types/Template1Interface";

defineProps<{
    title: string, description: string, products: BugZapperProduct[],
    buttonRatingText: string;
    buttonPurchaseText: string;

}>()
</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.products {
    &__title {
        font-size: 28px;
        font-weight: 800;
        margin-bottom: 20px;
    }

    &__headline {
        font-size: 20px;
        margin-bottom: 20px;
    }

    &-item {

        >article {
            border: 1px solid #000;
        }

        > :nth-child(1) {
            border: 3px solid var(--product-border-color);
        }

        > :nth-child(2) {
            border: 1px solid var(--product-border-color);
        }
    }

    &__item {
        margin-bottom: 50px;

        :last-child {
            margin-bottom: 0px;
        }
    }

    @media (max-width: 1024px) {
        &__title {
            text-align: center;
            font-size: 20px;
        }

        &__headline {
            font-size: 14px;
        }
    }
}
</style>