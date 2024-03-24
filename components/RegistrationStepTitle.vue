<template>
    <div>
        <h2 class="text-center text-2xl">{{ title }}</h2>
        <p class="text-center text-gray-600">{{ description }}</p>
        <hr class="my-8">
    </div>
</template>

<script setup>
const { title, description } = defineProps(["title", "description"])
</script>

<style lang="scss" scoped></style>