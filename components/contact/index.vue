<template>
    <div>
        <ArticleCategoryHeader category="Contact Us" :image="'article/contact-main.png'"
            description="Should you have any inquiries or require further information about our services, please feel free to reach out to us" />
        <div class="descriptions">
            <p class="description">
                We appreciate the interest and attention that Veristo receives daily, but due to the high influx of
                inquiries, we regretfully cannot respond to every message. We value your time and effort in reaching out to
                us, and we make every effort to address as many inquiries as possible.
            </p>
            <p class="description">
                For all queries or communications, we welcome you to get in touch with us at hello@veristo.com.
            </p>
            <p class="description">
                Thank you for understanding and we look forward to hearing from you.
            </p>
            <p class="description">
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
    min-height: 80vh;
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
        min-height: 0;
    }

    .description {
        margin-bottom: 15px;
    }

}
</style>