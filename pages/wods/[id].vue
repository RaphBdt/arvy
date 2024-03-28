<template>
    <div>
        <div class="border-b border-gray-200 mb-10 pb-5 sm:flex sm:items-center sm:justify-between">
            <h3 class="text-base font-semibold leading-6 text-gray-900">WOD #{{ id }}</h3>
            <!-- <div class="mt-3 sm:ml-4 sm:mt-0">
                <PrimaryButton @click="sendUpdatedWodToBackend" name="Mettre à jour" />
            </div> -->
        </div>

        <div v-if="exercises" class="min-h-[83vh] w-full rounded-lg background-custom-repeted-points flex flex-col items-center">
            <div class="flex flex-col items-start">
                <WodBlock v-for="block in wod.blocks" :exercises="exercises.exercises" :block="block" @update-wod="updateWod" />
                <WodAddBlock @add-exercises-block="addExercisesBlock" @add-break-block="addBreakBlock" />
            </div>
        </div>
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'dashboard'
})

let wod = ref([]);

const { id } = useRoute().params

let token = localStorage.getItem("token");
useFetch(`https://developpe-klnc5za-axul4nh3q5odm.fr-3.platformsh.site/api/wod/${id}`, {
    method: 'get',
    headers: {
        "Authorization": `Bearer ${token}`,
    },
    onResponse({ response }) {
        if(response.status === 200) {
            wod.value = response._data.wod;
        }
    }
})
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
        blockExercises: [
            {
                exercise: null,
                weight: null,
                rehearsals: null,
                time: null,
                advise: null,
                orderPosition: 0,
            }
        ],
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

<style lang="scss" scoped>

</style>