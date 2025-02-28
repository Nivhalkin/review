<template>
    <div>
        <HomeHeader :search="search" @updateSearch="updateSearch" />
        <HomeHeadLineDescription />
        <HomeProductCollection :search="computedProps" />
        <HomeFooterDescription />
        <HomeTopBrands :topBrands="categoryBrands" />
    </div>
</template>

<script setup lang="ts">
const search = ref("")

const updateSearch = (newValue: string) => {
    search.value = newValue;
};

const categoryBrands = ['health-topbrand-1.jpg', 'cooking-topbrand-2.jpg', 'outdoor-topbrand-3.jpg', 'beauty-topbrand-4.jpg', 'outdoor-topbrand-5.jpg']

const computedProps = computed(() => search.value)
</script>

<style lang="scss" scoped></style>