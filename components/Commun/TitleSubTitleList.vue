<template>
    <div>
        <h2 class="title">
            {{ props.title }}
        </h2>
        <div v-for="(section, key) in props.subSection" :key="`sub-section--${key}`">
            <h3 class="title__sub" v-if="section.title">
                {{ section.title }}
            </h3>
            <p class="description">
                <span v-for="descriptions in section.descriptions" :key="`description--${descriptions}`">
                    {{ descriptions }}
                </span>
            </p>
            <ul class="description description-list" v-if="section.list">
                <li v-for="listItem in section.list" :key="`list-item--${listItem}`">
                    {{ listItem }}
                </li>
            </ul>
        </div>
    </div>
</template>

<script setup lang="ts">
interface SubSection {
    title?: string;
    descriptions: string[];
    list?: string[];
}

const props = defineProps<{ title: string, subSection: SubSection[] }>();
</script>

<style lang="scss" scoped>
.title {
    font-size: 28px;
    font-weight: 800;
    margin-bottom: 24px;

    &__sub {
        font-size: 20px;
        margin-bottom: 20px;
    }

    @media (max-width: 1024px) {
        font-size: 20px;
        margin-bottom: 20px;

        &__sub {
            font-size: 16px;
        }
    }
}


.description {
    font-size: 20px;
    margin-bottom: 20px;

    &-list {
        padding-left: 20px;

        li {
            list-style: initial;
        }
    }

    span {
        margin-bottom: 15px;
        display: block;

        &:last-child {
            margin-bottom: 0;
        }
    }

    @media (max-width: 1024px) {
        font-size: 14px;
        margin-bottom: 15px;
    }
}
</style>