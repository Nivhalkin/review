<template>
    <div>
        <figure class="image">
            <nuxt-img format="webp" :src="`/images/${image}`" width="1080" height="490"
                alt="garden with brown table that handle a blue glass with flower inside" />
        </figure>
        <p class="description">
            <span v-for="(desc, index) in descriptions" :key="`description--${index}`">{{ desc }}</span>
        </p>
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{ image: string, descriptions: string[] }>()
</script>

<style lang="scss" scoped>
.image {
    overflow: hidden;
    margin-bottom: 20px;

    img {
        border-radius: 6px;
        aspect-ratio: auto 1080 / 490;
        width: 100%;
        height: auto;
    }

    @media (max-width: 1024px) {
        text-align: center;
        margin-bottom: 15px;
    }
}

.description {

    font-size: 20px;

    span {
        margin-bottom: 15px;
        display: block;

        :last-child {
            margin-bottom: 0;
        }
    }

    @media (max-width: 1024px) {
        font-size: 16px;
    }

}
</style>