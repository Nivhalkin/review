<template>
    <header>
        <h1 class="header__title">
            <span class="header__title--letter">V</span>erinews
        </h1>
        <div class="header__badge">
            Trending Topic
        </div>
    </header>
</template>

<script setup lang="ts">

</script>

<style scoped lang="scss">
.header {
    &__title {
        position: relative;
        background: #000000;
        color: #FFFFFF;
        font-size: 29px;
        padding: 15px 0;
        margin-bottom: 35px;
        font-weight: bold;

        &--letter {
            color: #58BF6F;
        }

        &::after {
            z-index: -1;
            content: '';
            position: absolute;
            left: -50vw;
            top: 0;
            background: #000000;
            height: 100%;
            width: 200vw;
        }
    }

    &__badge {
        width: fit-content;
        padding: 10px;
        color: #FFFFFF;
        background-color: #58BF6F;
        margin-bottom: 10px;
    }
}
</style>