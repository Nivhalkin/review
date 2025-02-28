<template>
    <section class="review">
        <header class="review__header">
            <nuxt-img loading="lazy" width="44" height="44" format="webp"
                :placeholder="img(`/images/avatar/${avatar}`, { h: 10, f: 'png', blur: 2, q: 50 })"
                class="review__avatar" alt="product best choice" :src="`/images/avatar/${avatar}`" fit="contain" />
            <div>
                <h4 class="review__name">{{ name }}</h4>
                <nuxt-img loading="lazy" width="108" height="20" format="webp"
                    :placeholder="img(`/images/reviews/review.png`, { h: 10, f: 'png', blur: 2, q: 50 })" alt="review"
                    src="/images/reviews/review.png" fit="contain" />
            </div>
        </header>
        <p class="review__header">
            {{ description }}
        </p>
    </section>
</template>

<script setup lang="ts">
const img = useImage()

defineProps<{ avatar: string, description: string, name: string }>();
</script>

<style scoped lang="scss">
.review {
    color: black;

    &__header {
        display: flex;
        align-items: center;
        gap: 8px;
        margin-bottom: 22px;
    }

    &__avatar {
        border-radius: 50%;
    }

    &__name {
        font-size: 14px;
        font-weight: 700;
        margin-bottom: 6px;
    }
}
</style>