<template>
    <section class="why">
        <ContentTitleDescription title="What Are Mosquitoes Zappers?"
                :descriptions="[
                    'Mosquito zappers are devices that attract and eliminate insects using electric shocks. The main component is an electrified grid, with ultraviolet (UV) light often used to lure insects, zapping them upon contact.',
                    'The device has a protective casing to ensure safety, allowing insects in while keeping larger creatures out. Some zappers have additional luring features like chemical attractants or CO2 emitters to trap various biting insects effectively.',
                    'When used correctly, mosquito zappers help create a comfortable space, allowing you to enjoy mosquito-free areas without the need for chemical sprays or swatters.']" />

                    <div id="scroll-1" :style="{paddingTop: '20px'}"></div>

        <ContentBenefitsAltOutdoor class="why__test" />
        <header class="why-header">
            <ContentTitleDescription id="scroll-2"
                title="How to Choose a High-Quality Mosquito Zapper?"
                :descriptions="[
                    'Choosing the right mosquito zapper involves considering a few key factors. As you look through our detailed comparisons, keep in mind the most important criteria like coverage area, mosquito draw strength, and durability ratings. Focusing on these fundamentals will help you identify effective products for reducing mosquito populations and creating enjoyable outdoor living spaces.']" />
        </header>

        <section class="why-highlight--split">
            <ContentHighlightSectionAlt v-bind="HighlightSection[0]">
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
                title: "Coverage Area",
                description: "Look at the square footage a zapper can protect. For residential backyards, you'll typically want at least 350 sq.ft of coverage. Wider zones allow the unit to reduce more flying insect populations on your property."
            },
            {
                title: "Insect Draw Strength",
                description: "The brightness of UV bulbs and configuration impacts how many mosquitoes are lured in and zapped. Look for powerful, high intensity bulbs placed in multiple directions to attract insects from all angles. "
            },
            {
                title: "Durability Construction",
                description: "Mosquitoes zappers are exposed to weather and constant use. Ensure the casing and components can withstand elements like rain without malfunctioning. Multi-year warranties often indicate reliable, robust products."
            },
            {
                title: "Safety Features",
                description: "Models with auto-off switches that activate if the unit falls over prevent risks to people and pets. Grids that fully enclose zapping wires also boost safety."
            },
            {
                title: "Cost Efficiency",
                description: "While higher upfront costs often deliver better value long-term, you can find high performing models for under $100. Compare ratings to get the most bang for your buck."
            }
        ]
    },
    {
        title: "What To Avoid:",
        type: "FAILURE",
        list: [
            {
                title: "Exposed Wires",
                description: "Models with unprotected zapping wires pose safety risks for people and pets. Ensure the grid is fully enclosed."
            },
            {
                title: "Toxic Chemical Lures",
                description: "Some low-end zappers use dangerous attractants. Make sure the unit relies solely on UV light."
            },
            {
                title: "Odor/Smoke",
                description: "Cheaply made zappers can release unpleasant burning smells. High quality units will zap cleanly without odors."
            },
            {
                title: "Small Coverage Areas",
                description: "Models that only protect up to 1/2 acre are less effective for larger yards and spaces. Look for at least 1 acre reach."
            },
            {
                title: "Dim, Single Bulbs",
                description: "Mosquitoes zappers need bright, wide-angled UV bulbs to attract insects. Avoid units with dim, low-watt bulbs or only one bulb."
            },
        ]
    }
]
</script>

<style lang="scss" scoped>
.why {

    &__test {
        margin-bottom: 40px;
    }

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