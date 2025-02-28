<template>
    <section class="best-choice">
        <h3 class="best-choice__heading">
            <CommunInlineText v-for="item in headerTitle" :key="item.toString()" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </h3>

        <h4 class="best-choice__title">
            <CommunInlineText v-for="item in title" :key="item.toString()" :text="item.text" :isBold="item.isBold"
                :textColor="item.textColor" :highlightColor="item.highlightColor" :isUnderlined="item.isUnderlined"
                :link="item.link" />
        </h4>

        <section class="best-choice-content">
            <figure class="best-choice-content-image">
                <nuxt-img loading="lazy" width="364" height="355" format="webp"
                    :placeholder="img(`/images/article/${image}`, { h: 10, f: 'png', blur: 2, q: 50 })"
                    class="best-choice-content-image__img" alt="product best choice" :src="`/images/article/${image}`"
                    fit="contain" />
            </figure>
            <div class="best-choice-content-info">
                <ul class="best-choice-content-info-list" v-if="kpiIsDisplayed">
                    <li class="best-choice-content-info-list__item" v-for="item in list" :key="item.text">
                        <CommunLineProgressBar :percentage="100" :style="{
                            '--linear-filled-color': item.backgroundColor
                        }">
                            <div class="best-choice-content-info-list__item-content" :style="{
                                '--list-item-color': item.textColor
                            }">
                                <p>
                                    {{ item.text }}
                                </p>
                                <p>
                                    {{ item.grade }}
                                </p>
                            </div>
                        </CommunLineProgressBar>
                    </li>
                </ul>
                <p class="best-choice-content-info__paragraph" v-for="item in description" :key="item.toString()">
                    <CommunInlineText v-for="description in item.paragraph" :key="description.text" :text="description.text"
                        :isBold="description.isBold" :textColor="description.textColor"
                        :highlightColor="description.highlightColor" :isUnderlined="description.isUnderlined"
                        :link="description.link" />
                </p>
                <div class="best-choice-content-info-button-content">
                    <NuxtLink
                        :class="`best-choice-content-info-button best-choice-content-info-button--${button.isXl ? 'xl' : 'm'}`"
                        :to="button.linkUrl">
                        {{ button.text }}
                    </NuxtLink>
                </div>

            </div>
        </section>
        <footer class="best-choice-footer">
            <div :style="{
                '--best-choice-footer-text-color': item.textColor
            }" v-for="item in footer" :key="item.text" class="best-choice-footer__item">
                <component :is="getRightIcon(item.image)" :currentColor="item.textColor"></component>
                <p>
                    {{ item.text }}
                </p>
            </div>
        </footer>
    </section>
</template>

<script setup lang="ts">
import InlineTextInterface from "~/types/InlineTextInterface";

const getRightIcon = (iconText: string) => {
    switch (iconText) {
        case 'from': return resolveComponent('icons/from')
        case 'guarantee': return resolveComponent('icons/guarantee')
        case 'shipping': return resolveComponent('icons/shipping')
        default: return resolveComponent('icons/from')
    }
}

const img = useImage()

defineProps<{
    headerTitle: InlineTextInterface[],
    title: InlineTextInterface[],
    image: string,
    list: {
        backgroundColor: string,
        textColor: string,
        text: string,
        grade: string
    }[],
    description: { paragraph: InlineTextInterface[] }[],
    button: {
        rounded: boolean,
        isXl: boolean,
        backgroundColor: string,
        borderColor: string,
        textColor: string,
        text: string,
        linkUrl: string
    },
    footer: {
        image: string,
        textColor: string,
        text: string
    }[]
    kpiIsDisplayed: boolean
}>()
</script>

<style scoped lang="scss">
.best-choice {
    background-color: var(--best-choice-background-color);
    border: 4px solid var(--best-choice-border-color);
    border-radius: var(--best-choice-border-radius);
    width: 100%;

    &-content {
        padding: 0 20px;
    }

    &__heading {
        padding: 20px 0;
        background: var(--best-choice-header-background-color);
        width: 100%;
        text-align: center;
        margin-bottom: 25px;
        font-weight: 600;
        font-size: var(--title-font-size);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    &__title {
        font-weight: 600;
        font-size: var(--title-font-size);
        text-align: center;
        margin-bottom: 23px;
    }

    &-content {
        display: flex;
        justify-content: center;
        align-items: center;

        &-image {
            flex: 3;
            margin-right: 17px;
            max-width: 380px;

            &__img {
                width: 100%;
                height: auto;
                object-fit: contain;
            }
        }

        &-info {
            width: 100%;
            flex: 5;

            &-list {
                margin-bottom: 18px;

                &__item {
                    margin-bottom: 5px;

                    &:last-child {
                        margin-bottom: 0px;
                    }

                    &-content {
                        width: 100%;
                        font-weight: 700;
                        color: var(--list-item-color);
                        font-size: 17px;
                        display: flex;
                        padding: 0 8px;
                        justify-content: space-between;
                        align-items: center;
                    }
                }
            }

            &__paragraph {
                font-size: var(--paragraph-font-size);
                margin-bottom: 20px;
            }

            &-button {
                &-content {
                    display: flex;
                }
                transition: all .3 ease;

                margin-bottom: 20px;

                background: var(--best-choice-button-background-color);
                color: var(--best-choice-button-text-color);
                box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
                text-align: center;
                border: 4px solid var(--best-choice-button-border-color);
                font-size: 25px;
                font-weight: 700;
                transition: background .3s ease;

                &--xl {
                    padding: 15px 74px;
                    border-radius: var(--best-choice-button-border-radius);
                }

                &--m {
                    padding: 16px 90px;
                    border-radius: var(--best-choice-button-border-radius);
                }

                &:hover {
                    background: #0A4927;
                }

            }
        }
    }

    &-footer {
        background-color: var(--best-choice-footer-background-color);
        padding: 20px 0;
        display: flex;
        align-items: center;
        justify-content: space-around;

        &__item {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            font-size: 18px;
            font-weight: 600;
            color: var(--best-choice-footer-text-color);
            gap: 20px;
        }
    }

    @media (max-width: 1024px) {
        &__heading {
            padding: 12px 0;
        }

        &-content {
            flex-direction: column;

            &-image {
                width: 180px;
                margin-right: 0px;
            }

            &-info {
                &-button {
                    font-size: 15px;
                }
            }
        }

        &-footer {
            &__item {
                font-size: 11px;
            }
        }
    }
}
</style>