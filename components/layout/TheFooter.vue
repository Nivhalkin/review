<template>
    <footer class="footer">
        <section class="footer-info">
            <h2 class="footer-info__title">
                <span>E</span>choique
            </h2>

        </section>
        <nav class="footer-navigation">
            <ul class="footer-navigation-grid">
                <li class="footer-navigation__item">
                    <NuxtLink to="/about">About</NuxtLink>
                </li>
                <li class="footer-navigation__item">
                    <NuxtLink to="/privacy">Privacy Policy</NuxtLink>
                </li>
                <li class="footer-navigation__item">
                    <NuxtLink to="/contact">Contact</NuxtLink>
                </li>
                <li class="footer-navigation__item">
                    <NuxtLink to="/terms">Terms of Use</NuxtLink>
                </li>
                <li class="footer-navigation__item">
                    <NuxtLink to="/disclaimer">Affiliate Disclosure</NuxtLink>
                </li>

            </ul>
        </nav>
        <div>
        <p class="footer-info-copyright--affiliate">*These statements have not been evaluated by the FDA Food & Drug Administration. These products are not intended to diagnose, treat, cure, or prevent any disease.</p>
            <p class="footer-info-copyright--affiliate">Note: We may receive compensation from some of the companies whose products are featured on this website. As a result, we receive payment when you purchase a product using the links on this website. The information contained within this site is not intended as a substitute for professional medical advice. If you have, expect to have, or suspect you may have any medical condition, you are urged to consult with a healthcare provider. All content, including text, graphics, images, and information, contained on or available through this website is for general information purposes only. Results do not necessarily reflect typical results from the use of these products. Please visit product websites for more information.</p>
            </div>
        <p class="footer-info-copyright">© 2023 Echoique, Inc. All rights reserved.</p>
    </footer>
</template>

<script setup>

</script>

<style lang="scss" scoped>
@import '~/assets/scss/_variables.scss';

.footer {
    background: $footer-header-background-color;
    color: $footer-header-text-color;
    width: 100vw;
    padding: 52px 100px 40px 90px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    &-info {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: flex-start;
        height: 100%;

        &__title {
            span {
                color: $logo-first-letter-color;
            }

            font-size: 30px;
            font-weight: 600;
            letter-spacing: -0.45px;
            margin-bottom: 38px;
        }

        &-copyright {
            font-size: 20px;
            color: $footer-copyright-text-color;
            margin-top: 42px;

            &--affiliate {
                color: #9B9B9B;
                font-size: 15px;
                margin-bottom: 20px;
                max-width: 70vw;
            }
        }
    }

    &-navigation {
        width: 100%;
        max-width: 70vw;
        &-grid {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 40px;
        }

        &__item {
            font-size: 20px;

            a {
                color: #FFF;
            }
        }
    }

    @media (max-width: 1024px) {
        padding: 39px 20px 23px 27px;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        height: auto;

        &-info {
            margin-bottom: 0px;

            &__title {
                margin-bottom: 30px;
            }


            &-copyright {
                font-size: 12px;
                margin-top: 20px;

                &--affiliate {
                    margin-bottom: 10px;
                    font-size: 10px;
                    max-width: inherit;
                }
            }
        }

        &-navigation {
            max-width: inherit;
            ul li {
                font-size: 12px;
            }

            &-grid {
                display: grid;
                grid-template-columns: repeat(2, 1fr);
                column-gap: 82px;
                row-gap: 22px;
                margin-top: 5px;
                margin-right: 10vw;
            }

            margin-bottom: 0px;
        }
    }
}
</style>