<template>
    <div class="importance">
        <h4 class="importance__title">
            {{ title }}
        </h4>
        <p class="importance__description">
            {{ description }}
        </p>
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{ title: string, description: string }>()
</script>

<style scoped lang="scss">
.importance {
    &__title {
        font-size: 28px;
        color: #5180DF;
        font-weight: 800;
        margin-bottom: 36px;
    }

    &__description {
        font-size: 20px;
        padding: 16px 20px;
        background: #5180df32;
    }

    @media (max-width: 1024px) {
        &__title {
            font-size: 20px;
            margin-bottom: 18px;
        }

        &__description {
            font-size: 14px;
            padding: 10px 5px;
        }
    }
}
</style>