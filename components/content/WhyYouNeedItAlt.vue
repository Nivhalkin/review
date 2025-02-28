<template>
    <section class="why">
        <header class="why-header">
            <ContentTitleDescription id="scroll-2"
                title="Which Ingredients Are Proven and What Precautions Are Essential When Choosing Nootropics?"
                :descriptions="[
                    'We cut through the hype and break down the specific nootropic ingredients scientifically shown to work, plus what to watch out for. Everything you need to pick the right brain-boosting formula.']" />
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
        title: "Top Ingredients to Look For:",
        type: "SUCESS",
        list: [
            {
                title: "Rhodiola Rosea",
                description: "Used for centuries to combat fatigue and enhance mood, studies now validate its ability to boost energy, concentration, and brain function, activating the brain's feel-good chemicals.*"
            },
            {
                title: "Lion’s Mane Mushrooms",
                description: "A mushroom rich in beneficial compounds, it's proven to stimulate brain cell growth, improve memory, focus, and clarity, and potentially help prevent cognitive decline.*"
            },
            {
                title: "Cordyceps Mushroom",
                description: "A distinctive mushroom known for boosting energy and mental strength. It enhances physical stamina as well as cognitive abilities like memory, focus, and reaction time.*"
            },
            {
                title: "Ashwagandha",
                description: "An age-old remedy for stress and lethargy, contemporary research shows its efficacy in reducing anxiety and depression while enhancing cognitive abilities such as memory, focus, and responsiveness.*"
            },
            {
                title: "Turmeric",
                description: "This bright yellow spice, rich in curcumin, is suggested by studies to increase dopamine and serotonin, enhancing memory, focus, and concentration, particularly for those with mild cognitive decline *"
            }
        ]
    },
    {
        title: "What To Avoid:",
        type: "FAILURE",
        list: [
            {
                title: "Low-quality ingredients",
                description: "Select products with top-tier ingredients, avoiding fillers. Trust nootropics with long-standing human usage, proven safety, and positive clinical trial outcomes.*"
            },
            {
                title: "Potential side effects",
                description: "Before using nootropics, be aware they might have side effects or interfere with existing medications. Always consult a physician first.*"
            },
            {
                title: "Lack of regulation",
                description: "OTC supplements aren't FDA-regulated. Prioritize purchases from trusted companies with independent product tests."
            },
            {
                title: "Hard To Read Label",
                description: "Opt for simple formulas with few ingredients backed by solid scientific evidence, as many trendy mixes lack proven benefits."
            },
            {
                title: "False or misleading marketing claims",
                description: "Research and read user reviews to avoid companies with misleading marketing tactics. Ensure genuine product effectiveness."
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
            margin-left: 27px;
            margin-bottom: 31px;
            font-style: italic;
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