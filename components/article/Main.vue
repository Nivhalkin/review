<template>
    <TheContent class="layout-content" />
</template>

<style lang="scss" scoped>
@import '~/assets/scss/main.scss';

.layout {

    &-header {
        margin-bottom: 39px;
    }

    &-content {
        margin-bottom: 76px;
    }

    @media (max-width: 1024px) {
        &-header {
            margin-bottom: 20px;
        }

        &-content {
            margin-bottom: 50px;
        }

    }
}
</style>