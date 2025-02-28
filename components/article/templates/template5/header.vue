<template>
    <header class="header">
        <div class="header-content">
            <h1 class="header__title">
                {{ title.split('_')[0] }}
            </h1>
            <p class="header__description">
                {{ subTitle }}
            </p>

            <div class="header-navigation">
                <div class="header-navigation__title">
                    {{ navigationTitle }}
                </div>
                <nav class="header-navigation-items">
                    <button class="header-navigation__item" v-for="(item, index) in navigationItems" :key="item"
                        @click="scrollToElement(index)">
                        {{ item }}
                    </button>
                </nav>
            </div>
        </div>
    </header>
</template>

<script setup lang="ts">
defineProps<{ title: string, subTitle: string, navigationTitle: string, navigationItems: string[] }>()

const scrollElementOne = ref<HTMLElement | null>(null);
const scrollElementTwo = ref<HTMLElement | null>(null);
const scrollElementThird = ref<HTMLElement | null>(null);
onMounted(() => {
    scrollElementOne.value = document?.getElementById('scroll-1')
    scrollElementTwo.value = document?.getElementById('scroll-2')
    scrollElementThird.value = document?.getElementById('scroll-3')
})



const scrollToElement = (index: number) => {
    const HtmlElement = [scrollElementOne, scrollElementTwo, scrollElementThird]
    if (HtmlElement[index]) {
        HtmlElement[index].value?.scrollIntoView({ behavior: 'smooth', })
    }
}
</script>

<style lang="scss" scoped>
.header {
    --spacing: 27px;
    background: var(--header-background);
    padding: 70px 0 150px 0;
    width: 100%;
    display: flex;
    justify-content: center;

    &-content {
        max-width: 900px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    &__title {
        text-align: center;
        font-size: 47px;
        font-weight: 600;
        line-height: normal;
        margin-bottom: var(--spacing);
    }

    &__description {
        font-size: 16px;
        font-weight: 500;
        margin-bottom: var(--spacing);
        text-align: center;
    }

    &-navigation {
        display: flex;
        align-items: center;
        justify-content: center;

        &__title {
            font-size: 17px;
            font-weight: 600;
            margin-right: var(--spacing);
        }

        &-items {
            display: flex;
            align-items: center;
            justify-content: flex-start;
        }

        &__item {
            position: relative;
            background: transparent;
            padding: 18px 34px;
            margin-right: 27px;
            font-size: 17px;
            font-weight: 600;
            border-radius: 40px;
            border: 1px solid var(--header-navigation-border-color);
            border-radius: var(--header-navigation-border-radius);

            &:last-child {
                margin-right: 0;
            }

            &:hover::after {
                opacity: 1;
            }

            &::after {
                content: '';
                position: absolute;
                left: -3px;
                bottom: -3px;
                width: 100%;
                height: 100%;
                border-radius: 40px;
                border: 3px solid var(--header-navigation-border-color);
                transition: opacity 0.2s ease;
                opacity: 0;
            }
        }
    }

    @media (max-width: 1024px) {
        padding: 22px 18px 15px 22px;
        --spacing: 13px;

        &__title {
            font-size: 28px;
        }

        &-navigation {
            display: none;
        }
    }

}
</style>