<template>
    <li class="icon-line" :style="{ alignItems: (isAlt || !!!title) ? 'center' : 'flex-start' }">
        <figure v-if="!isAlt && !showIcon">
            <nuxt-img format="webp" :src="`/images/${props.image}`" width="30px" :height="isAlt ? '18px' : '30px'"
                :alt="`${props.image.split('.png')[0]}`" />
        </figure>
        <div>
            <h4 v-if="props.title" class="icon-line__title" :style="{ fontWeight: isBold ? '700' : isAlt ? '400' : '600' }">
                {{ props.title }}
            </h4>
            <div v-if="props.description" class="icon-line-description">
                <span v-if="!!showIcon && props.description" class="icon-line__dot">.</span>
                <p class="icon-line__description">
                    {{ props.description }}
                </p>
            </div>
        </div>
    </li>
</template>

<script setup lang="ts">

const props = defineProps<{ showIcon?: boolean, title?: String, description?: String, image: String; isBold?: boolean, isAlt?: boolean }>();

</script>

<style lang="scss" scoped>
.icon-line {
    display: flex;
    gap: 19px;
    align-items: flex-start;

    &__dot {
        font-size: 25px;
        margin-bottom: 15px;
        margin-right: 7px;
        line-height: 0;
    }

    &__title {
        font-size: 20px;
        font-weight: 600;
        margin-bottom: 10px;
    }

    &-description {
        display: flex;
        align-items: center;
    }

    &__description {
        color: #000;
        font-size: 16px;
        font-weight: 400;
    }

    @media (max-width: 1024px) {
        gap: 15px;

        figure img {
            width: 20px;
            height: 20px;
        }

        &__title {
            margin-bottom: 3px;
            font-size: 15px;
        }

        &__description {
            font-size: 14px;
        }
    }
}
</style>