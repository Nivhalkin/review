<template>
    <header class="header">
        <div class="header-content">
            <h1 class="header__title">
                {{ title.split('_')[0] }}
            </h1>
        </div>
    </header>
</template>

<script setup lang="ts">
defineProps<{ title: string }>()

</script>

<style lang="scss" scoped>
.header {
    --spacing: 27px;
    background: var(--header-background);
    padding: 70px 0 150px 0;
    width: 100%;
    display: flex;
    justify-content: center;

    &-content {
        max-width: 75vw;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    &__title {
        text-align: center;
        font-size: 47px;
        font-weight: 600;
        line-height: normal;
        margin-bottom: var(--spacing);
    }

    &__description {
        font-size: 16px;
        font-weight: 500;
        margin-bottom: var(--spacing);
        text-align: center;
    }

    @media (max-width: 1024px) {
        padding: 22px 18px 15px 22px;
        --spacing: 13px;

        &-content {
            max-width: inherit;
        }

        &__title {
            font-size: 28px;
        }
    }

}
</style>