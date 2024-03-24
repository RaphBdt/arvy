<template>
    <NuxtLink :to="link" :class="`flex justify-center rounded-md bg-${color}-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-${color}-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-${color}-600`">{{ name }}</NuxtLink>
</template>

<script setup>
    const { name, link, color } = defineProps(['name', 'link', 'color'])
</script>

<style scoped>

</style>