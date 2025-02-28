<template>
    <header class="header">
        <h2 class="header__title">
            Explore our analyses.Trust our tips.Choose with <span> confidence</span>
        </h2>
        <form class="header-form">
            <div class="header-form-search">
                <label class="header-form-search__label" for="search">search product</label>
                <input v-model="childData" @input="updateSearch" class="header-form-search__input" type="text" name="search"
                    id="search">
                <button type="submit" class="header-form-search__submit">
                    Search
                </button>
            </div>

        </form>
        <figure class="header--background">
            <nuxt-img format="webp" preload loading="eager" src="/images/home-main-image.png" alt="person that type on a laptop"
                fit="cover" />
        </figure>
    </header>
</template>

<script setup lang="ts">
const emit = defineEmits(['updateSearch'])

const { search } = defineProps<{
    search: string,
}>();

const childData = ref(search);

const updateSearch = () => {
    emit('updateSearch', childData.value)
}

</script>

<style lang="scss" scoped>
.header {
    position: relative;
    padding: 106px 0 163px 118px;
    width: 100%;

    &--background {
        position: absolute;
        overflow: hidden;
        left: 0;
        top: 0;
        background: linear-gradient(0deg, rgba(0, 0, 0, 0.60) 0%, rgba(0, 0, 0, 0.60) 100%), url(<path-to-image>), lightgray 50% / cover no-repeat;
        width: 100%;
        height: 100%;

        img {
            width: 100%;
            height: 100%;
        }
    }

    &__title,
    &-form {
        max-width: 663px;
    }

    &__title {
        z-index: 1;
        color: white;
        margin-bottom: 48px;
        font-size: 40px;
        position: relative;


        >span {
            color: #04B273;
        }
    }

    &-form {
        z-index: 1;
        position: relative;
        width: 100%;
        background: white;
        height: 63px;
        border-radius: 60px;

        &-search {
            position: relative;
            align-items: center;
            justify-content: center;
            display: flex;
            height: 100%;
            gap: 20px;


            &__label {
                width: 0;
                height: 0;
                overflow: hidden;
                position: absolute;
            }

            &__input {
                width: 100%;
                height: 80%;
                padding-left: 20px;
            }

            &__submit {
                margin-right: 20px;
                color: #fff;
                background: #04B273;
                font-size: 18px;
                padding: 9px 44px;
                border-radius: 60px;
                transition: background .3s ease;

                &:hover {
                    background: #038757;
                }
            }
        }
    }

    @media (max-width: 1024px) {
        padding: 20px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        min-height: 210px;

        &--background img {
            object-fit: cover;
        }

        &__title {
            font-size: 20px;
            margin-bottom: 24px;
            text-align: center;
        }

        &-form {
            height: 30px;
            width: 70vw;



            &-search {
                &__input {
                    font-size: 12px;
                }

                &__submit {
                    font-size: 15px;
                    padding: 4px 16px;
                    margin-right: 5px;
                }
            }
        }
    }
}
</style>