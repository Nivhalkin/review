<template>
    <div class="subheader">
        <div class="subheader-content">
            <div class="subheader-content__date">Latest update: {{ formattedDate }}</div>
            <div class="subheader-content-bar">
                <button @click="openDialog(dialogData[1])">ADVERTISER DISCLOSURE</button>
                <div class="subheader-content--separator">|</div>
                <button @click="openDialog(dialogData[0])">HOW WE RANK</button>
                <Transition>
                    <div v-if="isOpen" class="subheader-content-bar__dialog">
                        <div class="subheader-content-bar__dialog-info">
                            <h4 class="subheader-content-bar__dialog-info__title">
                                {{ currentDialog.title }}
                            </h4>
                            <button @click="isOpen = false">
                                <figure>
                                    <nuxt-img format="webp" alt="checked blue icon" src="/images/close-icon.png"
                                        width="30px" height="30px" />
                                </figure>
                            </button>
                        </div>

                        <p class="subheader-content-bar__dialog__description">
                            {{ currentDialog.description }}
                        </p>
                    </div>
                </Transition>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, reactive } from "vue"

const dialogData = [
    {
        title: "HOW WE RANK",
        description: "Products on our site may be linked to businesses that provide us compensation or where we have a stake.\
    This may affect how and where products are shown, including their order.Product rankings can change and not all products\
     in their categories are included.Factors influencing rankings can be the user device, location, day, time, cookie data, \
     and any data we generate on this site."
    },
    {
        title: "ADVERTISER DISCLOSURE",
        description: "The product rankings on our site are generated from our personal perspectives, understanding, and beliefs.\
         We do not evaluate all available products within a specific category, and the opinions shared on this platform are solely\
          ours.We are able to offer free comparisons due to referral commissions we receive from various companies featured and analyzed\
           on our website."
    }
]

let isOpen: Ref<boolean> = ref(false);
let currentDialog = reactive({
    title: "", description: ""
});

const openDialog = (data: { title: string, description: string }) => {
    currentDialog.title = data.title;
    currentDialog.description = data.description;
    if (!isOpen.value) {
        isOpen.value = true
    }
}

let formattedDate: String;
const formatDateInEnglish = (date: Date) => {
    const monthNames = [
        'January', 'February', 'March', 'April', 'May', 'June', 'July',
        'August', 'September', 'October', 'November', 'December'
    ];

    const month = monthNames[date.getMonth()];
    const day = date.getDate();
    const year = date.getFullYear();

    return `${month} ${day}, ${year}`;
}
const currentDate = new Date();
currentDate.setDate(currentDate.getDate() - 5);
formattedDate = formatDateInEnglish(currentDate);


</script>


<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.subheader {
    color: $app-text-color;
    width: 100vw;
    height: 39px;
    background-color: $subheader-background-color;
    display: flex;
    justify-content: center;
    align-items: center;

    &-content {
        font-size: 14px;
        max-width: $breakpoint-max-width--desktop;
        display: flex;
        justify-content: space-between;
        width: 100%;

        &--separator {
            display: none;
        }

        div:last-child {
            display: flex;
            justify-content: flex-end;
            gap: 50px;
        }

        &-bar {
            position: relative;

            button {
                background: transparent;
                color: black;
            }

            &__dialog {
                padding: 30px 10px;
                display: block !important;
                background: #fff;
                position: absolute;
                top: 40px;
                right: 0;
                box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);

                &-info {
                    display: flex;
                    justify-content: space-between;
                    align-items: flex-end;
                    margin-bottom: 17px;

                    &__title {
                        font-size: 18px;
                        font-weight: 700;
                    }
                }

                &__description {
                    font-size: 13px;
                    min-width: min(400px, 82vw);
                }

            }
        }
    }



    @media (max-width: 1024px) {
        justify-content: flex-end;
        padding-right: 19px;

        &-content {
            justify-content: flex-end;
            font-size: 8px;

            &--separator {
                display: block;
                font-size: 10px;
                padding-bottom: 2px;
            }

            &__date {
                display: none;
            }

            div:last-child {
                display: flex;
                justify-content: flex-end;
                align-items: center;
                gap: 10px;
            }

            &-bar button {
                font-size: 8px;
            }

            &-bar__dialog {
                padding: 10px;

                &-info {
                    align-items: flex-start;
                    margin-bottom: 22px;

                    &__title {
                        font-size: 15px;
                    }

                    figure img {
                        width: 20px;
                        height: 20px;
                    }
                }


                &__description {
                    font-size: 12px;
                }
            }


        }

    }
}
</style>