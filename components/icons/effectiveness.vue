<template>
    <svg class="effectiveness" xmlns="http://www.w3.org/2000/svg" width="50" height="51" viewBox="0 0 50 51" fill="none">
        <g clip-path="url(#clip0_200_87)">
            <path
                d="M37.097 28.7743C37.9287 28.3951 39.0627 28.0917 40.8772 28.1675C43.5234 28.2434 45.6404 29.4569 47.0013 31.5048C47.3792 31.884 50.2522 37.1934 46.472 43.0336C45.5647 44.4747 44.6575 45.7641 43.5234 46.9019C42.6917 47.7362 41.8601 48.798 40.8017 49.1014C39.4408 49.5565 38.1554 48.4946 36.7946 48.4946H36.719C35.3581 48.4946 34.0728 49.4806 32.7119 49.1014C31.5779 48.798 30.8218 47.7362 29.9901 46.9019C28.8561 45.7641 27.8732 44.4747 27.0416 43.0336C23.2613 37.1934 26.1343 31.9599 26.5123 31.5048C27.8732 29.4569 29.9901 28.2434 32.6363 28.1675"
                :stroke="currentColor" stroke-width="2.5" stroke-miterlimit="10" stroke-linecap="round"
                stroke-linejoin="round" />
            <path d="M34.0728 31.808C34.0728 31.808 36.6433 33.1689 39.3651 31.808" :stroke="currentColor"
                stroke-width="2.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
            <path
                d="M35.5845 24.2233C38.0038 18.9899 43.145 21.1895 43.145 21.1895C43.145 21.1895 41.9353 23.1614 40.1208 24.9818C39.3647 25.7403 38.3819 25.9678 36.3405 25.7403"
                :stroke="currentColor" stroke-width="2.5" stroke-miterlimit="10" stroke-linecap="round"
                stroke-linejoin="round" />
            <path d="M37.0966 28.7741C37.0966 28.7741 36.7942 26.1953 33.3164 22.7063" :stroke="currentColor"
                stroke-width="2.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
            <path
                d="M34.8286 17.397V12.0877L25 2.22749H3.0746C2.24294 2.22749 1.5625 2.91012 1.5625 3.74444V47.7359C1.5625 48.5703 2.24294 49.2529 3.0746 49.2529H25.7561"
                :stroke="currentColor" stroke-width="2.5" stroke-miterlimit="10" stroke-linecap="square"
                stroke-linejoin="round" />
            <path d="M34.0726 12.0876H25.756C25.3024 12.0876 25 11.7843 25 11.3292V8.29527" :stroke="currentColor"
                stroke-width="2.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
            <path d="M13.6592 20.4309H28.7801" :stroke="currentColor" stroke-width="2.5" stroke-miterlimit="10"
                stroke-linecap="round" stroke-linejoin="round" />
            <path d="M13.6592 26.4987H24.9999" :stroke="currentColor" stroke-width="2.5" stroke-miterlimit="10"
                stroke-linecap="round" stroke-linejoin="round" />
            <path d="M13.6592 32.5664H21.2197" :stroke="currentColor" stroke-width="2.5" stroke-miterlimit="10"
                stroke-linecap="round" stroke-linejoin="round" />
            <path d="M13.6592 38.6342H21.2197" :stroke="currentColor" stroke-width="2.5" stroke-miterlimit="10"
                stroke-linecap="round" stroke-linejoin="round" />
            <path d="M7.61084 12.0876H15.9274" :stroke="currentColor" stroke-width="2.5" stroke-miterlimit="10"
                stroke-linecap="round" stroke-linejoin="round" />
            <path
                d="M8.36708 21.9478C9.20216 21.9478 9.87917 21.2686 9.87917 20.4309C9.87917 19.5931 9.20216 18.9139 8.36708 18.9139C7.53197 18.9139 6.85498 19.5931 6.85498 20.4309C6.85498 21.2686 7.53197 21.9478 8.36708 21.9478Z"
                :fill="currentColor" />
            <path
                d="M8.36708 28.0156C9.20216 28.0156 9.87917 27.3364 9.87917 26.4987C9.87917 25.6609 9.20216 24.9817 8.36708 24.9817C7.53197 24.9817 6.85498 25.6609 6.85498 26.4987C6.85498 27.3364 7.53197 28.0156 8.36708 28.0156Z"
                :fill="currentColor" />
            <path
                d="M8.36708 34.0834C9.20216 34.0834 9.87917 33.4042 9.87917 32.5665C9.87917 31.7287 9.20216 31.0495 8.36708 31.0495C7.53197 31.0495 6.85498 31.7287 6.85498 32.5665C6.85498 33.4042 7.53197 34.0834 8.36708 34.0834Z"
                :fill="currentColor" />
            <path
                d="M8.36708 40.1512C9.20216 40.1512 9.87917 39.472 9.87917 38.6342C9.87917 37.7965 9.20216 37.1173 8.36708 37.1173C7.53197 37.1173 6.85498 37.7965 6.85498 38.6342C6.85498 39.472 7.53197 40.1512 8.36708 40.1512Z"
                :fill="currentColor" />
        </g>
        <defs>
            <clipPath id="clip0_200_87">
                <rect width="50" height="50.1604" fill="white" transform="translate(0 0.659973)" />
            </clipPath>
        </defs>
    </svg>
</template>

<script setup lang="ts">
defineProps<{ currentColor: string }>()

</script>

<style scoped lang="scss">
.effectiveness {
    @media (max-width: 1024px) {
        width: 50px;
        height: 37px;
    }
}</style>