<template>
    <section class="highlight">
        <h3 :class="`highlight__title`">
            {{ title }}
        </h3>
        <section>
            <ul class="highlight-list">
                <p class="icon-line__description" ContentIconLine v-for="(item, index) in list"
                    :key="`highlight-list-item--${index}`">
                    {{ item }}
                </p>
            </ul>
        </section>
    </section>
</template>

<script lang="ts" setup>

defineProps<{ title: String, list: string[] }>();

</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';


.highlight {
    background: $section-background-color;

    &__title {
        font-size: 20px;
        font-weight: 600;
        text-align: center;
        margin-bottom: 34px;
        color: var(--list-header-title-color);
        text-align: left;
        padding: 8px 30px;
        background: var(--list-header-background-color);
    }

    &-list {
        display: flex;
        flex-direction: column;
        gap: 10px;
        padding-left: 30px;
        padding-bottom: 21px;
        font-size: 20px;
    }

    @media (max-width: 1024px) {
        // padding: 28px 20px;

        &__title {
            font-size: 16px;
            margin-bottom: 22px;
        }
    }

}
</style>