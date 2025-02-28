<template>
    <section class="benefits">
        <header>
            <h3 class="benefits__title">
                {{ title }}
            </h3>
        </header>
        <ul class="benefits-list">
            <ContentIconLine v-for=" item in listItem" :key="item.description" :title="item.title"
                :description="item.description" image="checked-blue-icon.png" />
        </ul>

    </section>
</template>

<script setup lang="ts">
defineProps<{ title: string, listItem: { title: string, description: string }[] }>()
</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.benefits {
    background-color: $section-background-color;
    padding-bottom: 23px;
    display: flex;
    flex-direction: column;
    border-radius: 6px;
    overflow: hidden;
    border-radius: 5px;
    margin-top: 10px;

    &__title {
        padding: 15px 0;
        text-align: center;
        margin-bottom: 37px;
        font-size: 28px;
        font-weight: 800;
        background: var(--benefits-header-color);
        color: var(--benefits-title-color);
    }

    &-list {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        row-gap: 25px;
        column-gap: 80px;
        font-size: 20px;
        padding: 0 10px;
        margin-left: auto;
        margin-right: auto;
        padding: 0px 31px 40px 26px;

        &-item {
            display: flex;
            align-items: center;
            gap: 19px;
            line-height: normal;
        }
    }

    @media (max-width: 1024px) {

        margin: 0 0;

        &__title {
            font-size: 16px;
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

    @media (max-width: 500px) {

        &-list {
            &-item {
                font-size: 14px;
            }

        }
    }
}
</style>