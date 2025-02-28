<template>
    <svg width="24" height="22" viewBox="0 0 27 25" fill="none" xmlns="http://www.w3.org/2000/svg">
        <g id="check-deinitive 1">
            <path id="Vector" d="M8.7998 12.5L12.0998 15.625L17.5999 9.375" :stroke="currentColor" stroke-width="2.2"
                stroke-linecap="round" stroke-linejoin="round" />
            <path id="Vector_2"
                d="M20.9005 4.16675H5.5004C4.89288 4.16675 4.40039 4.63311 4.40039 5.20841V19.7918C4.40039 20.3671 4.89288 20.8334 5.5004 20.8334H20.9005C21.5081 20.8334 22.0005 20.3671 22.0005 19.7918V5.20841C22.0005 4.63311 21.5081 4.16675 20.9005 4.16675Z"
                :stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" />
        </g>
    </svg>
</template>

<script setup lang="ts">
defineProps<{ currentColor: string }>()

</script>

<style scoped lang="scss"></style>