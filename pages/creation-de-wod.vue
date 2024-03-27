<template>
    <div v-if="exercises" class="min-h-[83vh] w-full rounded-lg background-custom-repeted-points flex flex-col items-center">
        <WodCreationBlock :exercises="exercises.exercises" />
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'dashboard'
})

let token = localStorage.getItem("token");
const { data: exercises } = await useFetch('https://developpe-klnc5za-axul4nh3q5odm.fr-3.platformsh.site/api/exercise', {
    method: 'get',
    headers: {
        "Authorization": `Bearer ${token}`,
    },
})

</script>

<style scoped>

</style>