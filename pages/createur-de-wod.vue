<template>
    <div v-if="errorMessage">
        <Alert :message="errorMessage" type="error" />
    </div>

    <div class="border-b border-gray-200 mb-10 pb-5 sm:flex sm:items-center sm:justify-between">
      <h3 class="text-base font-semibold leading-6 text-gray-900">Créateur de WODs</h3>
      <div class="mt-3 sm:ml-4 sm:mt-0">
        <PrimaryButton @click="sendWod" name="Sauvegarder" />
      </div>
    </div>
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

let errorMessage = ref(null)

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

async function sendWod() {
    let token = localStorage.getItem("token");
    if (token && wod.value) {
        await useFetch('https://developpe-klnc5za-axul4nh3q5odm.fr-3.platformsh.site/api/wod/full', {
            method: 'post',
            headers: {
                "Content-Type": "application/json",
                "Authorization": `Bearer ${token}`,
            },
            body: wod.value,
            onResponse({ response }) {
                if (response.status === 200) {
                    errorMessage.value = null
                    navigateTo('/gestion-des-wods')
                } else {
                    errorMessage.value = "Une erreur est survenue."
                }
            }
        })
    } else {
        errorMessage.value = "Une erreur est survenue."
    }
}
</script>

<style scoped>

</style>