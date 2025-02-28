<template>
    <div>
        <h2 class="title">
            {{ title }}
        </h2>
        <p v-if="description" class="description">
            {{ description }}
        </p>
    </div>
</template>

<script setup lang="ts">

const props = defineProps<{ title: string, description?: string }>();

</script>

<style lang="scss" scoped>
.title {
    font-size: 44px;
    font-weight: 700;
    padding: 0 2%;
    text-align: center;
    margin-bottom: 28px;

    @media (max-width: 1024px) {
        font-size: 28px;
        margin-bottom: 10px;
        padding: 0;
    }
}

.description {
    padding: 0 10%;
    text-align: center;
    font-size: 19px;
    margin-bottom: 21px;

    @media (max-width: 1024px) {
        padding: 0;
        font-size: 14px;
    }
}
</style>