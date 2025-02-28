<template>
    <div class="footer">
        <p class="footer__description">
            We review brands to help you make
            a smarter purchase decision.
        </p>
    </div>
</template>

<style lang="scss" scoped>
.footer {
    color: white;
    padding: 55px 0;
    background: #00301E;
    width: 100%;
    display: flex;
    justify-content: center;

    &__description {
        max-width: 607px;
        font-size: 35px;
        font-weight: 600;
        text-align: center;
    }

    @media (max-width: 1024px) {
        padding: 20px 0;

        &__description {
            font-size: 16px;
        }
    }
}
</style>