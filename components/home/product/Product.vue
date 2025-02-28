<template>
    <section class="product">
        <header class="product-header">
            <figure class="product-header-img">
                <nuxt-img format="webp" fit="cover" :alt="title.split('_')[0]" :src="`/images/${image}`" />
            </figure>
        </header>

        <div class="product-content">
            <div class="product-content-details">
                <h4 class="product-content-details__title">
                    {{ title.split('_')[0] }}
                </h4>

                <p class="product-content-details__description">{{ description }}</p>
            </div>

        </div>

        <footer class="product-footer">
            <NuxtLink class="product-footer__button" :to="link">
                Read
            </NuxtLink>

        </footer>
    </section>
</template>

<script setup lang="ts">

defineProps<{ title: string, description: string, link: string, image: string }>()

</script>

<style lang="scss" scoped>
.product {
    display: flex;
    flex-direction: column;

    &-header {
        &-img {
            width: 100%;
            height: 320px;
            overflow: hidden;
            border-radius: 6px;

            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }
    }

    &-content {
        padding: 0 22px;
        display: flex;
        height: 100%;

        &-details {
            padding: 19px 9px;
            background: #FFF;
            border-radius: 6px;
            margin-top: -50px;
            margin-bottom: 25px;

            &__title {
                font-size: 20px;
                font-weight: 700;
                margin-bottom: 17px;
                text-align: center;
            }

            &__description {
                font-size: 15px;
            }
        }


    }

    &-footer {
        margin-top: auto;

        &__button {
            width: 100%;
            color: #fff;
            background: #04B273;
            font-size: 15px;
            font-weight: 700;
            padding: 9px 0;
            border-radius: 60px;
            transition: background .3s ease;
            display: block;
            text-align: center;

            &:hover {
                background: #038757;
            }
        }
    }

    @media (max-width: 1024px) {
        &-header {
            &-img {
                height: 160px;
            }
        }

        &-content {
            padding: 0 5px;
            display: flex;
            height: 100%;

            &-details {
                margin-bottom: 10px;
                padding: 5px 5px;
                margin-top: -27px;

                &__title {
                    font-size: 14px;
                    font-weight: 700;
                    margin-bottom: 10px;
                    text-align: center;
                }

                &__description {
                    text-align: center;
                    font-size: 12px;
                }
            }
        }

        &-footer {
            &__button {

                font-size: 14px;
                padding: 6px 0;
            }
        }
    }

}
</style>