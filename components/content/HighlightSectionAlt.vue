<template>
    <section class="highlight" :style="{
        'background': props.background === HighlightType.SUCESS ? '#EFFFF9' : props.background === HighlightType.FAILURE ? '#FFF2F1' : ''
    }">
        <h3 :class="`highlight__title highlight__title--${type.toLocaleLowerCase()}`"
            :style="{ 'text-align': props.background && 'left' }">
            {{ title }}
        </h3>
        <section>
            <ul class="highlight-list">
                <ContentIconLine v-for="(item, index) in list" :key="`highlight-list-item--${index}`" :title="item.title"
                    :description="item.description" :image="image" isBold />
            </ul>
            <slot></slot>
        </section>
    </section>
</template>

<script lang="ts" setup>

enum HighlightType {
    SUCESS = "SUCESS",
    FAILURE = "FAILURE",
    NEUTRAL = "NEUTRAL"
}

const props = defineProps<{ background?: HighlightType, title: String, type: HighlightType, list: Array<{ title: String, description: String }> }>();

const image = (() => {
    switch (props.type) {
        case HighlightType.SUCESS:
            return "checked-green-icon.png";

        case HighlightType.FAILURE:
            return "stop-red-icon.png"

        case HighlightType.NEUTRAL:
            return "line-blue-icon.png"
    }
})()

</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';


.highlight {
    background: $section-background-color;
    border-radius: 5px;
    overflow: hidden;

    &__title {
        font-size: 28px;
        font-weight: 800;
        text-align: center;
        margin-bottom: 37px;
        color: white;
        padding: 20px 0;

        &--sucess {
            background: $section-sucess-color;
        }

        &--failure {
            background: $section-failure-color;
        }

        &--neutral {
            background: $section-neutral-color;
        }
    }

    &-list {
        display: flex;
        flex-direction: column;
        gap: 28px;
        padding: 0px 31px 40px 26px;
    }

    @media (max-width: 1024px) {

        &__title {
            font-size: 20px;
            margin-bottom: 22px;
        }
    }

}
</style>