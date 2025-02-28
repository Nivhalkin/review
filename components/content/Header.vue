<template>
    <header>
        <CommunHeader :title="title" :description="description" />
    </header>
</template>

<script setup lang="ts">

defineProps<{ title: string, description: string }>()

</script>