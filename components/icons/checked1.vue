<template>
    <svg class="checked" width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
        <g id="icons8-check (1) 1">
            <g id="Group">
                <g id="Group_2">
                    <path id="Vector"
                        d="M20.97 4.3126C20.638 4.32432 20.3333 4.5001 20.1575 4.78135L10.7513 19.172L4.65751 13.9064C4.39579 13.6349 4.00321 13.5333 3.64188 13.6466C3.28251 13.7579 3.01493 14.0626 2.95243 14.4337C2.88993 14.8067 3.04032 15.1817 3.34501 15.4064L10.3138 21.4376C10.5325 21.6231 10.8216 21.7052 11.1048 21.6642C11.3899 21.6212 11.6419 21.4591 11.7981 21.2189L21.845 5.87511C22.0599 5.56065 22.0774 5.1544 21.8919 4.82237C21.7063 4.49229 21.3489 4.29502 20.97 4.3126Z"
                        :fill="currentColor" />
                </g>
            </g>
        </g>
    </svg>
</template>

<script setup lang="ts">
defineProps<{ currentColor: string }>()

</script>

<style scoped lang="scss">
.checked {
    @media (max-width: 1024px) {
        width: 20px;
        height: 20px;
    }
}
</style>