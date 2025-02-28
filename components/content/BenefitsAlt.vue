<template>
    <section class="benefits" id="scroll-1">
        <header>
            <h3 class="benefits__title">
                Potential Benefits of Nootropics
            </h3>
        </header>
        <ul class="benefits-list">
            <li class="benefits-list-item">
                <figure>
                    <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                        height="30px" />
                </figure>
                Sharper focus and concentration*
            </li>
            <li class="benefits-list-item">
                <figure>
                    <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                        height="30px" />
                </figure>
                Increased motivation and alertness*
            </li>
            <li class="benefits-list-item">
                <figure>
                    <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                        height="30px" />
                </figure>
                Enhanced learning and memory recall*
            </li>
            <li class="benefits-list-item">
                <figure>
                    <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                        height="30px" />
                </figure>
                Immunity support*
            </li>
            <li class="benefits-list-item">
                <figure>
                    <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                        height="30px" />
                </figure>
                Elevated mood and reduced stress*
            </li>
        </ul>

    </section>
</template>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.benefits {
    background-color: $section-background-color;
    padding-bottom: 23px;
    display: flex;
    flex-direction: column;
    border-radius: 6px;
    overflow: hidden;
    border-radius: 5px;

    &__title {
        padding: 15px 0;
        text-align: center;
        margin-bottom: 37px;
        font-size: 28px;
        font-weight: 800;
        background: $section-neutral-color;
        color: #FFF;
    }

    &-list {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        row-gap: 25px;
        column-gap: 80px;
        font-size: 20px;
        padding: 0 10px;
        margin-left: auto;
        margin-right: auto;

        &-item {
            display: flex;
            align-items: center;
            gap: 19px;
            line-height: 16px;
        }
    }

    @media (max-width: 1024px) {

        margin: 0 0;

        &__title {
            font-size: 16px;
            margin-bottom: 21px;
        }

        &-list {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
            font-size: 20px;

            &-item {
                font-size: 16px;

                figure img {
                    width: 20px;
                    height: 20px;
                }
            }

        }
    }

    @media (max-width: 500px) {

        &-list {
            &-item {
                font-size: 14px;
            }

        }
    }
}
</style>