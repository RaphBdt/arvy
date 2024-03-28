<template>
    <div v-if="exercises" class="min-h-[83vh] w-full rounded-lg background-custom-repeted-points flex flex-col items-center">
        <div class="flex flex-col items-start">
            <WodBlock v-for="n in allTheBlocks" :exercises="exercises.exercises" :type="n.type" />
            <WodAddBlock @add-exercises-block="addExercisesBlock" @add-break-block="addBreakBlock" />
        </div>
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'dashboard'
})

let allTheBlocks = ref([
    {
        type: 'exercises'
    }
]);

let token = localStorage.getItem("token");
const { data: exercises } = await useFetch('https://developpe-klnc5za-axul4nh3q5odm.fr-3.platformsh.site/api/exercise', {
    method: 'get',
    headers: {
        "Authorization": `Bearer ${token}`,
    },
})

function addExercisesBlock() {
    let newObject = {
        type: 'exercises'
    };
    allTheBlocks.value.push(newObject)
}

function addBreakBlock() {
    let newObject = {
        type: 'break'
    };
    allTheBlocks.value.push(newObject)
}
</script>

<style scoped>

</style>