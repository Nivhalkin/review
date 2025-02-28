<template>
    <div class="top-brands">
        <h3 class="top-brands__title">
            Top Brands
        </h3>
        <div class="top-brands-brands">
            <figure class="top-brands-brands-image" v-for="brand in topBrands" :key="`top-brands-image--${brand}`">
                <nuxt-img format="webp" fit="cover" alt="checked blue icon" :src="`/images/article/${brand}`" width="150px"
                    height="150px" />
            </figure>
        </div>
    </div>
</template>

<script setup lang="ts">

defineProps<{ topBrands: string[] }>()

</script>

<style lang="scss" scoped>
.top-brands {
    background: #F1F1E9;
    padding: 50px 0 69px 0;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    &__title {
        font-size: 40px;
        font-weight: 700;
        margin-bottom: 62px;
    }

    &-brands {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 62px;

        &-image {
            border-radius: 50%;
            overflow: hidden;
            width: 150px;
            height: 150px;
        }
    }

    @media (max-width: 1024px) {
        padding: 20px 0 30px 0;
        overflow: hidden;

        &__title {
            font-size: 20px;
            margin-bottom: 31px;
        }

        &-brands {
            gap: 10px;


            &-image {
                width: 65px;
                height: 65px;

                img {
                    width: 100%;
                    height: 100%;
                }
            }
        }
    }
}
</style>