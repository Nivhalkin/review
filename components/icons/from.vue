<template>
    <svg class="from" width="75" height="50" viewBox="0 0 75 50" fill="none" xmlns="http://www.w3.org/2000/svg">
        <g id="Frame">
            <path id="Vector" d="M71.7868 1.68311H1.55176V47.7795H71.7868V1.68311Z" :stroke="currentColor" stroke-width="2"
                stroke-miterlimit="10" stroke-linejoin="round" />
            <path id="Vector_2" d="M31.987 1.68311V20.5407H1.55176" :stroke="currentColor" stroke-width="2"
                stroke-miterlimit="10" stroke-linejoin="round" />
            <path id="Vector_3"
                d="M32.4251 11.1177H71.5815M32.4251 20.5527H71.5815M2.30469 29.3137H71.5815M3.0577 38.0746H71.5815"
                :stroke="currentColor" stroke-width="2" stroke-linecap="square" />
        </g>
    </svg>
</template>

<script setup lang="ts">
defineProps<{ currentColor: string }>()

</script>

<style scoped lang="scss">
.from {
    @media (max-width: 1024px) {
        width: 50px;
        height: 37px;
    }
}
</style>