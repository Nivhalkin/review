<template>
    <div>
        <header class="header">
            <h1 class="header__title">
                <span>E</span>choique
            </h1>
            <nav class="header-navigation">
                <ul class="header-navigation-list">
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/">
                            Home Page
                        </NuxtLink>
                    </li>
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/article/beauty">
                            Beauty
                        </NuxtLink>
                    </li>
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/article/cooking">
                            Cooking
                        </NuxtLink>
                    </li>
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/article/health">
                            Health & Wellness
                        </NuxtLink>
                    </li>
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/article/outdoor">
                            Outdoor
                        </NuxtLink>
                    </li>
                </ul>
            </nav>
            <TransitionGroup name="list" tag="div">
                <figure :key="1" v-show="!isOpen" @click="isOpen = true" class="header-menu header-menu--open">
                    <nuxt-img format="webp" alt="open menu icon" src="/images/menu-icon.png" width="20" height="20" />
                </figure>

                <figure :key="2" v-show="isOpen" @click="isOpen = false" class="header-menu header-menu--close">
                    <nuxt-img format="webp" alt="close menu icon" src="/images/menu-close-icon.png" width="22"
                        height="22" />
                </figure>
            </TransitionGroup>
        </header>
        <Transition>
            <div class="header-open" v-show="isOpen">
                <ul class="header-navigation-list" @click="isOpen = false">
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/">
                            Home Page
                        </NuxtLink>
                    </li>
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/article/beauty">
                            Beauty
                        </NuxtLink>
                    </li>
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/article/cooking">
                            Cooking
                        </NuxtLink>
                    </li>
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/article/health">
                            Health & Wellness
                        </NuxtLink>
                    </li>
                    <li class="header-navigation-list__item">
                        <NuxtLink to="/article/outdoor">
                            Outdoor
                        </NuxtLink>
                    </li>
                </ul>
            </div>
        </Transition>
        <TheSubHeader v-if="!hideSubHeader" />
    </div>
</template>

<script setup lang="ts">

const { hideSubHeader } = defineProps<{ hideSubHeader?: Boolean }>();

const isOpen = ref(false)
watch(isOpen, (newValue, oldValue) => {
    if (newValue) {
        document.body.style.overflow = 'hidden'
    }
    else {
        document.body.style.overflow = 'initial'
    }
})
</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.header {
    position: relative;
    width: 100vw;
    height: 84px;
    background-color: $footer-header-background-color;
    color: $footer-header-text-color;
    display: flex;
    align-items: center;
    z-index: 2;

    &-open {
        display: none;
        position: fixed;
        top: 44px;
        height: calc(100vh);
        overflow: hidden;
        width: 100vw;
        background: $footer-header-background-color;
        z-index: 3;
    }

    &__title {
        font-size: 30px;
        font-weight: 600;
        letter-spacing: -0.45px;

        span {
            color: $logo-first-letter-color;
        }

        position: absolute;
        top: 50%;
        left: 92px;
        transform: translate3d(0, -50%, 0);
    }

    &-navigation {
        width: 100vw;

        &-list {
            margin: auto;
            max-width: $breakpoint-max-width--desktop;
            display: flex;
            justify-content: flex-end;
            gap: 20px;

            &__item {
                font-weight: 500;
                font-size: 16px;

                a {
                    color: #FFF;
                }

                &:hover {
                    cursor: pointer;
                }
            }
        }
    }

    &-menu {

        &--open,
        &--close {
            display: none;
        }
    }

    @media (max-width: 1024px) {
        height: 44px;

        &-open {
            display: block;
        }

        &__title {
            font-size: 22px;
            left: 16px;
        }

        &-navigation {
            display: none;
        }

        &-navigation-list {
            color: #FFF;
            height: 100vh;
            flex-direction: column;
            padding: 0 17px;
            gap: 39px;
            max-width: inherit;
            justify-content: flex-start;
            padding-top: 10vh;

            &__item {
                font-size: 15px;
                padding-bottom: 22px;
                border-bottom: 1px solid #FFF;
                width: 100%;
            }
        }

        &-menu {
            right: 16px;
            position: absolute;
            bottom: 50%;
            transform: translate(0, 50%);

            &--open,
            &--close {
                height: 22px;
                display: block;
            }

        }

    }
}
</style>