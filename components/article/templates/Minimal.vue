<template>
    <div class="content">
        <div class="content-container">
            <CommunHeader :title="props.article.title" :description="props.article.subTitle" />
            <CommunImageDescription :image="props.article.image" :descriptions="props.article.descriptions" />
            <ArticleImportance class="content-importance" :title="props.article.importanceTitle"
                :description="props.article.importanceDescription" />
            <ContentTitleDescription class="content-title-description"
                :title="props.article.titleDescriptionSections[0].title"
                :descriptions="props.article.titleDescriptionSections[0].descriptions" />
            <ContentTitleDescription class="content-title-description--2"
                :title="props.article.titleDescriptionSections[1].title"
                :descriptions="props.article.titleDescriptionSections[1].descriptions" />
            <ContentHighlightSection class="content-highlight" v-bind="props.article.lookFor" />
            <ContentHighlightSection class="content-highlight" v-bind="props.article.avoid" />
            <ContentTitleDescription class="content-conclusion" v-bind="props.article.conclusion" />
            <CommunButtonBackToTop text="Back to top" />
        </div>
    </div>
</template>

<script setup lang="ts">
import MinimalTemplate from '@/types/MinimalInterface';

const props = defineProps<{ article: MinimalTemplate }>()


</script>

<style lang="scss" scoped>
.content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    &-container {
        max-width: 75vw;
    }

    &-importance {
        margin-bottom: 29px;
    }

    &-title-description {
        margin-bottom: 49px;

        &--2 {
            margin-bottom: 59px;
        }
    }

    &-highlight {
        margin-bottom: 30px;
    }

    &-conclusion {
        margin-bottom: 70px;
    }

    @media (max-width: 1024px) {
        &-container {
            max-width: inherit;
            padding: 0 20px;
        }

        &-importance {
            margin-bottom: 15px;
        }

        &-title-description {
            margin-bottom: 25px;

            &--2 {
                margin-bottom: 59px;
            }
        }

        &-highlight {
            margin-bottom: 15px;
        }

        &-conclusion {
            margin-bottom: 35px;
        }

        &-header {
            margin-bottom: 15px;
        }

    }

}
</style>