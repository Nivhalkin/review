<template>
    <div>
        <h2 v-if="title" :id="props.id" class="title">
            {{ props.title }}
        </h2>
        <p class="description">
            <span v-for="desc in props.descriptions" :key="`description--${desc}`">
                {{ desc }}
            </span>
        </p>
    </div>
</template>

<script setup lang="ts">

const props = defineProps<{ title?: string, descriptions: string[], id?: string }>();
</script>

<style lang="scss" scoped>
.title {
    font-size: 28px;
    font-weight: 800;
    margin-bottom: 24px;

    @media (max-width: 1024px) {
        font-size: 20px;
        margin-bottom: 20px;
    }
}


.description {
    font-size: 20px;
    margin-bottom: 20px;

    span {
        margin-bottom: 15px;
        display: block;

        &:last-child {
            margin-bottom: 0;
        }
    }

    @media (max-width: 1024px) {
        font-size: 16px;
        margin-bottom: 15px;
    }
}
</style>