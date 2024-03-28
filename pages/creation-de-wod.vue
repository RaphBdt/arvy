<template>
    <div v-if="exercises" class="min-h-[83vh] w-full rounded-lg background-custom-repeted-points flex flex-col items-center">
        <div class="flex flex-col items-start">
            <WodBlock v-for="block in wod.blocks" :exercises="exercises.exercises" :block="block" @update-wod="updateWod" />
            <WodAddBlock @add-exercises-block="addExercisesBlock" @add-break-block="addBreakBlock" />
        </div>
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'dashboard'
})

let wod = ref({
    name: 'wod',
    blocks: [
        {
            parentBlock: null,
            rehearsals: null,
            time: null,
            break: false,
            childBlocks:[],
            blockExercises: [],
            blockResults: [],
            orderPosition: 0
        }
    ]
});

let token = localStorage.getItem("token");
const { data: exercises } = await useFetch('https://developpe-klnc5za-axul4nh3q5odm.fr-3.platformsh.site/api/exercise', {
    method: 'get',
    headers: {
        "Authorization": `Bearer ${token}`,
    },
})

function addExercisesBlock() {
    let exerciseBlock = {
        parentBlock: null,
        rehearsals: null,
        time: null,
        break: false,
        childBlocks:[],
        blockExercises: [],
        blockResults: [],
        orderPosition: wod.value.blocks.slice(-1)[0].orderPosition + 1
    };
    wod.value.blocks.push(exerciseBlock)
}

function addBreakBlock() {
    let breakBlock = {
        parentBlock: null,
        rehearsals: null,
        time: null,
        break: true,
        childBlocks:[],
        blockExercises: [],
        blockResults: [],
        orderPosition: wod.value.blocks.slice(-1)[0].orderPosition + 1
    };
    wod.value.blocks.push(breakBlock)
}

function updateWod(data) {
    updateObject(wod.value.blocks.find((element) => element.orderPosition === data.orderPosition), data)
}

function updateObject(originalObj, newObj) {
    for (let key in newObj) {
        if (newObj[key] === undefined) {
            originalObj[key] = null;
        } else {
            originalObj[key] = newObj[key];
        }
    }
    return originalObj;
}
</script>

<style scoped>

</style>