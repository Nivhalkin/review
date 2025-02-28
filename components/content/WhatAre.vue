<template>
    <div>
        <ContentTitleDescription title="What Are Whitening Strips?"
            :descriptions="[
                'Whitening strips have a gel containing ingredients that help lift stains from your teeth enamel. The main active ingredient is peroxide. It seeps into your enamel and chemically reacts with stain molecules to break them down.',
                'The gel also includes hydrating botanical extracts like aloe. These soothe and prevent sensitivity while you whiten your teeth. Some strips even incorporate desensitizing agents into the formula to further minimize discomfort.',
                'When used as directed, the ingredients in the whitening gel interact to gently yet effectively brighten your smile by a few shades or more. The strips allow you to whiten from home without complicated dental procedures.']" />
        <section class="benefits" id="scroll-1">
            <header>
                <h3 class="benefits__title">
                    Benefits of Good Whitening Strips
                </h3>
            </header>
            <ul class="benefits-list">
                <li class="benefits-list-item">
                    <figure>
                        <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                            height="30px" />
                    </figure>
                    Delivers noticeable whitening results.
                </li>
                <li class="benefits-list-item">
                    <figure>
                        <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                            height="30px" />
                    </figure>
                    Offers brighter teeth in minimal time
                </li>
                <li class="benefits-list-item">
                    <figure>
                        <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                            height="30px" />
                    </figure>
                    At-home application without dentist visits.
                </li>
                <li class="benefits-list-item">
                    <figure>
                        <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                            height="30px" />
                    </figure>
                    Minimizes tooth and gum discomfort
                </li>
                <li class="benefits-list-item">
                    <figure>
                        <nuxt-img format="webp" alt="checked blue icon" src="/images/checked-blue-icon.png" width="30px"
                            height="30px" />
                    </figure>
                    Simple, straightforward application process.
                </li>
            </ul>

        </section>
    </div>
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
        background: #08BF7D;
        color: #FFF;
    }

    &-list {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        row-gap: 25px;
        column-gap: 80px;
        font-size: 20px;
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
            padding: 0 10px;

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