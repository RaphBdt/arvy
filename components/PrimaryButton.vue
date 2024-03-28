<template>
    <NuxtLink v-if="link" :to="link" :class="`flex justify-center rounded-md bg-violet-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-violet-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-violet-600`">{{ name }}</NuxtLink>
    <button v-else type="button" :class="`flex justify-center rounded-md bg-violet-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-violet-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-violet-600`">{{ name }}</button>
</template>

<script setup>
    const { name, link } = defineProps(['name', 'link'])
</script>

<style scoped>

</style>