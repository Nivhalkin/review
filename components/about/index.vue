<template>
    <div>
        <ArticleCategoryHeader category="About Us" :image="'article/about-main.png'"
            description="Your Trusted Partner for Comprehensive, Unbiased Product Reviews and Comparisons." />
        <div class="descriptions">
            <p class="description">
                Welcome to the <strong>Echoique.com</strong> family! We are a dedicated team of product review specialists
                passionate about
                providing you with the most comprehensive, unbiased reviews and comparisons across outdoor, beauty, health &
                wellness, and cooking product niches. We exist to facilitate your purchasing decisions, ensuring they are
                well-informed and perfectly suited to your needs and preferences.
            </p>
            <p class="description">
                At Echoique, our team doesn't just buy and test products. We go beyond, meticulously mining online
                platforms for user reviews and feedback, scrutinizing product specifications, and consulting industry
                experts. Our review process is exhaustive and detail-oriented, aiming to present a well-rounded view of each
                product's performance and value.
            </p>
            <p class="description">
                Our commitment to transparency and honesty is unwavering. As such, we want to disclose that we may receive
                compensation from companies for some products linked on our site. While this might influence the way these
                products are displayed, it in no way impacts the authenticity of our reviews. Your trust in our evaluations
                remains our utmost priority.
            </p>
            <p class="description">
                Please note that our product rankings are not static. They might vary based on a host of factors, including
                your device, location, date, time, and cookie data. Consequently, not all available products in a specific
                category may be featured in our rankings.
                Even though we receive referral commissions from some of the companies whose products are showcased on our
                site, our commitment to unbiased reporting is uncompromised. Each review and comparison is drawn from our
                own perspectives and beliefs, offering you an authentic, reliable source of information.
            </p>
            <p class="description">
                Our team at <strong>Echoique.com</strong> brings together a love for exploration, a pursuit of beauty, a
                commitment to health & wellness, and a passion for cooking. We’re more than just a review website - we are a
                community bound by a shared curiosity and a commitment to making informed purchasing decisions.

            </p>
            <p class="description">
                We're thrilled to have you onboard and can't wait to help you discover, compare, and choose the best
                products in the vast world of outdoor, beauty, health & wellness, and cooking items. Let's begin this
                journey together.
            </p>
            <p class="description">
                Best Regards,<br />
                The Echoique.com Team
            </p>
        </div>

    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.descriptions {
    padding: 35px 84px;
    font-size: 20px;
    background-color: #F1F1E9;
    border-top-right-radius: 60px;
    border-top-left-radius: 60px;
}

.description {
    margin-bottom: 30px;
}

@media (max-width: 1024px) {
    .descriptions {
        border-top-right-radius: 30px;
        border-top-left-radius: 30px;
        padding: 20px;
        font-size: 14px;
    }

    .description {
        margin-bottom: 15px;
    }

}
</style>