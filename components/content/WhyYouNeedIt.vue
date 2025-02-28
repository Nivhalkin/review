<template>
    <section class="why">
        <header class="why-header">
            <ContentTitleDescription id="scroll-2" :title="title" :descriptions="descriptions" />
        </header>

        <section class="why-highlight--split">
            <ContentHighlightSection v-bind="lookfor" :style="{
                '--header-background-color': lookfor.headerBackgroundColor,
                '--header-title-color': lookfor.titleColor
            }">
                <p class="why-highlight__slot" v-if="lookfor?.extraDescription">{{ lookfor.extraDescription }}</p>
            </ContentHighlightSection>
            <ContentHighlightSection v-bind="avoid" :style="{
                '--header-background-color': avoid.headerBackgroundColor,
                '--header-title-color': avoid.titleColor
            }" />
        </section>
        <ContentHighlightSection v-if="more" v-bind="more" :style="{
            '--header-background-color': more.headerBackgroundColor,
            '--header-title-color': more.titleColor
        }" />
    </section>
</template>

<script setup lang="ts">
defineProps<{ title: string, descriptions: string[], lookfor: Object, avoid: Object, more?: Object }>()
</script>

<style lang="scss" scoped>
.why {

    &-header {
        &__title {
            font-size: 28px;
            font-weight: 800;
            margin-bottom: 24px;
        }

        &__description {
            font-size: 20px;
            margin-bottom: 20px;
        }
    }

    &-highlight {
        &--split {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;

            * {
                flex: 1;
            }
        }

        &__slot {
            color: #646161;
            font-size: 9px;
            margin-left: 27px;
            margin-bottom: 31px;
            font-style: italic;
            margin-top: -15px;
        }
    }

    @media (max-width: 1024px) {
        &-highlight {
            &--split {
                flex-direction: column;
            }
        }

        &-header {
            &__title {
                font-size: 20px;
                margin-bottom: 20px;
            }

            &__description {
                font-size: 14px;
                margin-bottom: 15px;
            }
        }
    }

}
</style>