<template>
    <div>
        <p>WOD #{{ id }}</p>
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'dashboard'
})

const { id } = useRoute().params
</script>

<style lang="scss" scoped>

</style>