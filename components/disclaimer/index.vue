<template>
    <div class="disclaimer">
        <CommunHeader title="Affiliate Disclosure" />
        <ContentTitleDescription class="disclaimer__description" :descriptions="paragraphs" />
        <CommunButtonBackToTop text="Back to top" />
    </div>
</template>

<script setup lang="ts">

const paragraphs = [
    'Welcome to Echoique, your trusted destination for impartial and comprehensive reviews of products in diverse categories, including the great outdoors, beauty, education, health & wellness.',
    'Our purpose at Echoique is to equip consumers with transparent, reliable, and meticulously researched data about their potential purchases. Our sophisticated rating algorithm critically assesses every product based on a multitude of factors, such as ingredient or material composition, product safety, proof of efficacy, and clinical research, supplemented by the insights of our experienced reviewers.',
    'In the spirit of full transparency, it\'s important to note that some links on our site may be affiliate links. This means we might earn a commission if you click on a link or make a purchase using that link. It\'s important to understand that any compensation received does not, and will not, influence our reviews and recommendations. Our primary focus always remains to provide genuine, impartial advice. Our affiliations support our mission to continue offering high-quality, detailed reviews.',
    'Echoique stands as a paragon of impartiality, and our compliance with Federal Regulation and the Federal Trade Commission’s guidelines is unwavering. We openly declare any monetary or proprietary relationships with manufacturers, where present, to ensure our readers have all requisite information when making purchasing decisions. All views and opinions expressed in our reviews are solely those of our experienced authors, who investigate and review each product extensively.', 
    'Please note that Echoique has no affiliation with the Food and Drug Administration. None of the products featured on our site are designed to diagnose, treat, cure, or prevent any diseases. Echoique does not offer medical advice, and we strongly urge you to engage with a qualified healthcare provider for any health-related questions or issues.',
    'The content presented on Echoique, including but not limited to text, graphics, reviews, and ratings, is sourced from product manufacturers and is intended strictly for informational purposes. We advise that you review all information provided by the manufacturers, both online and on the physical product packaging, meticulously prior to making any purchase.',
    'Our devoted team is committed to providing the most current and accurate information. However, given that product details are subject to change, we cannot guarantee the absolute accuracy of all published data. All products, brand names, and other trademarks mentioned within our site are the property of their respective trademark owners.',
    'At Echoique, our goal is to equip you with comprehensive knowledge to make informed purchasing decisions. Your faith in our commitment to integrity, transparency, and superior research is our highest reward. Together, let\'s navigate the diverse realm of products that can enhance our daily lives.'
    
]

</script>

<style lang="scss" scoped>
.disclaimer {
    width: 100vw;
    margin: auto;

    &__description {
        margin-bottom: 105px;
    }

    @media (max-width: 1024px) {
        &__description {
            margin-bottom: 50px;
        }
    }
}
</style>