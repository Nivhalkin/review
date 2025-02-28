<template>
    <section class="why">
        <header class="why-header">
            <ContentTitleDescription id="scroll-2"
                title="Key Considerations in Selecting Whitening Strips"
                :descriptions="[
                    'Choosing the right whitening strips involves considering a few key factors. As you look through our detailed comparisons, keep in mind the most important criteria like safe peroxide levels, built-in desensitizers, and clinical testing. Focusing on these fundamentals will help you identify effective products for achieving the brighter smile you want.']" />
        </header>

        <section class="why-highlight--split">
            <ContentHighlightSectionAlt v-bind="HighlightSection[0]">
                <p class="why-highlight__slot">*Individual results may vary</p>
            </ContentHighlightSectionAlt>
            <ContentHighlightSectionAlt v-bind="HighlightSection[1]" />
        </section>
    </section>
</template>

<script setup>
const HighlightSection = [
    {
        title: "What To Look For:",
        type: "SUCESS",
        list: [
            {
                title: "Peroxide",
                description: "This is the active ingredient that penetrates the enamel and lifts stains. Look for a percentage around 5-30% for the best balance of safety and efficacy. Too little won't whiten much while too much increases sensitivity risks."
            },
            {
                title: "Built-in desensitizers (potassium nitrate)",
                description: "Desensitizing ingredients help minimize discomfort during and after whitening by calming nerve activity in the teeth. Look for potassium nitrate or similar agents in the formula."
            },
            {
                title: "Hydrating ingredients",
                description: "Hydrators prevent dryness of the gums and teeth during the whitening process. They soothe and maintain healthy enamel. Glycerin and aloe vera are common options."
            },
            {
                title: "A thin, moldable strip",
                description: "The strip should be flexible enough to adapt closely to the contours and alignment of your teeth for maximum coverage. Rigid strips with poor moldability won't whiten evenly."
            },
            {
                title: "An experienced brand",
                description: "Go with well-established companies that have perfected strip technology over many years and extensive trials. Their expertise results in proven safety and effectiveness."
            }
        ]
    },
    {
        title: "What To Avoid:",
        type: "FAILURE",
        list: [
            {
                title: "High peroxide levels",
                description: "Extremely high levels increase the chances of tooth and gum sensitivity during and after whitening. Anything above 30% provides minimal additional whitening for much greater irritation risks."
            },
            {
                title: "Irritating ingredients",
                description: "Some ingredients like SD alcohol can dry out the mouth and cause gum irritation. Look for hydrating, soothing formulas."
            },
            {
                title: "Slippery strips",
                description: "If the strip lacks stick and keeps moving, the gel won't stay against your teeth long enough to work. The fit needs to be snug."
            },
            {
                title: "DIY recipes",
                description: "Home mixtures haven't undergone proper safety and efficacy testing. Stick to proven commercial products."
            },
            {
                title: "Expired product",
                description: "The ingredients degrade in potency over time. Always check the expiration date before using and discard expired strips."
            },
        ]
    }
]
</script>

<style lang="scss" scoped>
.why {

    &-header {
        &__title {
            font-size: 28px;
            font-weight: 800;
            margin-bottom: 24px;
        }

        &__description {
            font-size: 20px;
            margin-bottom: 20px;
        }
    }

    &-highlight {
        &--split {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;

            * {
                flex: 1;
            }
        }

        &__slot {
            color: #646161;
            font-size: 9px;
            font-style: italic;
            margin-left: 27px;
            margin-bottom: 31px;
            margin-top: -15px;
        }
    }

    @media (max-width: 1024px) {
        &-highlight {
            &--split {
                flex-direction: column;
            }
        }

        &-header {
            &__title {
                font-size: 20px;
                margin-bottom: 20px;
            }

            &__description {
                font-size: 14px;
                margin-bottom: 15px;
            }
        }
    }

}
</style>