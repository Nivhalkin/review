<template>
    <section class="benefits" id="scroll-1">
        <header>
            <h3 class="benefits__title">
                {{ title }}
            </h3>
        </header>
        <ul class="benefits-list">
            <li class="benefits-list-item" v-for="text in listItem" :key="text">
                <figure>
                    <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                        height="30px" />
                </figure>
                {{ text }}
            </li>
        </ul>

    </section>
</template>

<script setup lang="ts">
defineProps<{ title: string, listItem: string[] }>()
</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.benefits {
    background-color: $section-background-color;
    padding-bottom: 23px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 6px;
    overflow: hidden;

    >header {
        width: 100%;
    }

    &__title {
        text-align: center;
        margin-bottom: 37px;
        font-size: 28px;
        font-weight: 800;
        color: var(--benefits-title-color);
        padding: 15px 0;
        text-align: center;
        background: var(--benefits-header-color);
    }

    &-list {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        row-gap: 25px;
        column-gap: 28px;
        font-size: 20px;
        padding: 0 10px;

        &-item {
            display: flex;
            align-items: center;
            gap: 19px;
            line-height: 16px;
        }
    }

    @media (max-width: 1024px) {

        margin: 0 0;

        &__title {
            font-size: 20px;
            margin-bottom: 21px;
        }

        &-list {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
            font-size: 20px;

            &-item {
                font-size: 16px;

                figure img {
                    width: 20px;
                    height: 20px;
                }
            }

        }
    }
}
</style>