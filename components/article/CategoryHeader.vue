<template>
    <header class="header">
        <h2 class="header__title">
            {{ formatTitle(category) }}
        </h2>
        <p class="header__description">
            {{ description }}
        </p>
        <figure class="header--background">
            <nuxt-img format="webp" preload loading="eager" :src="`/images/${image}`" alt="person that type on a laptop" fit="cover" />
        </figure>
    </header>
</template>

<script setup lang="ts">
defineProps<{
    category: string,
    description: string,
    image: string
}>();

const formatTitle = (title: string) => {

    if (title === 'health') {
        return title.charAt(0).toUpperCase() + title.slice(1) + ' & Wellness'
    }

    return title.charAt(0).toUpperCase() + title.slice(1)
}

</script>

<style lang="scss" scoped>
.header {
    position: relative;
    width: 100%;
    height: 476px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    &--background {
        position: absolute;
        overflow: hidden;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;

        img {
            object-fit: cover;
            width: 100%;
        }
    }

    &__title {
        z-index: 1;
        color: white;
        margin-bottom: 10px;
        font-size: 40px;
        font-weight: 800;
    }

    &__description {
        text-align: center;
        color: #FFF;
        z-index: 1;
        font-size: 18px;
        max-width: 635px;
    }

    @media (max-width: 1024px) {
        min-height: 210px;
        height: 200px;

        &--background img {
            height: 100%;
        }

        &__title {
            font-size: 20px;
            margin-bottom: 10px;
        }

        &__description {
            font-size: 12px;
            max-width: 90vw;
        }
    }
}
</style>