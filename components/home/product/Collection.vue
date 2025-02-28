<template>
    <div class="collection">
        <div v-if="routeCategory">
            <div class="collection-products">
                <section class="collection-product-list">
                    <HomeProduct v-for="(product, index) in singleCategory?.products"
                        :key="`collection-product-list--${index}`" :image="product.image" :title="product.title"
                        :description="product.description" :link="product.link" />
                </section>
            </div>
        </div>
        <template v-else>
            <div v-for="category in filteredCategories" :key="`category--${category.title}`">
                <h3 class="collection-product__title">
                    {{ formatTitle(category.title) }}
                </h3>
                <div class="collection-products">
                    <section class="collection-product-list">
                        <HomeProduct v-for="(product, index) in category.products"
                            :key="`collection-product-list--${index}`" :image="product.image" :title="product.title"
                            :description="product.description" :link="product.link" />
                    </section>
                </div>
            </div>
        </template>

    </div>
</template>

<script setup lang="ts">
import { computed } from "vue"

const { data, pending } = await useFetch('/api/articles');

let articlesClone: any = {
    beauty: null,
    outdoor: null,
    health: null,
    cooking: null

};

data?.value?.map(article => {
    articlesClone[article.id] = article.data.filter((article: any) => article.isShownInCollection)
})

const formatTitle = (title: string) => {

    if (title === 'health') {
        return title.charAt(0).toUpperCase() + title.slice(1) + ' & Wellness'
    }

    return title.charAt(0).toUpperCase() + title.slice(1)
}

const props = defineProps<{
    search: string;
    routeCategory?: string
}>();

let singleCategory: any;
let filteredCategories: any

if (props.routeCategory) {
    singleCategory = (() => {
        if (props.routeCategory) {
            return {
                title: props.routeCategory, products: articlesClone[props.routeCategory].map((article: any, index: number) => {
                    const linkURL = article.title.replaceAll(' ', '-')
                    return { title: article?.title, description: article?.subTitle ? article.subTitle : '', image: article?.image, link: `/article/${props.routeCategory}/${linkURL}` }
                })
            }
        }
    })()
}

else {
    const categories = (() => {
        const formattedCategories = Object.keys(articlesClone).map(category => {
            return {
                title: category, products: articlesClone[category].map((article: any, index: number) => {
                    const linkURL = article.title.replaceAll(' ', '-')
                    return { title: article?.title ? article.title : article.header.title, description: article?.subTitle ? article.subTitle : '', image: article?.image, link: `/article/${category}/${linkURL}` }
                })
            }
        })
        return formattedCategories
    })()

    filteredCategories = computed(() => {
        const cloneCategories: Array<{ title: string, products: Array<{ title: string, description: string, image: string, link: string }> }> = JSON.parse(JSON.stringify(categories))

        let filteredCategoriesWithSearchQuery = cloneCategories.map(category => {
            const filteredProducts = category.products.filter(product => product.title.includes(props.search) || product.description.includes(props.search))
            category.products = filteredProducts

            return category

        }).filter(category => category.products.length > 0)

        return filteredCategoriesWithSearchQuery
    })
}

</script>

<style lang="scss" scoped>
.collection {
    background: #F1F1E9;
    padding: 71px;
    display: flex;
    flex-direction: column;
    gap: 72px;
    border-radius: 60px;

    &-products {
        display: flex;
        // justify-content: center;
        width: 100%;
    }

    &-product {
        &__title {
            font-size: 40px;
            margin-bottom: 42px;
            font-weight: 700;
        }

        &-list {
            display: flex;
            // justify-content: center;
            align-items: flex-start;
            flex-wrap: wrap;
            gap: 66px;

            >* {
                align-self: stretch;
                max-width: 324px;
                min-width: 324px;
            }
        }

    }

    @media (max-width: 1024px) {
        padding: 20px 10px;
        gap: 20px;
        border-radius: 30px;

        &-product {
            &__title {
                font-size: 20px;
                margin-bottom: 21px;
            }

            &-list {
                gap: 10px;

                >* {
                    max-width: calc(50vw - 15px);
                    min-width: calc(40vw);
                }
            }
        }
    }
}
</style>