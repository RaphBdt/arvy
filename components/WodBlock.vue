<template>
  <div v-if="!block.break" class="flex items-center">
    <div class="flex flex-col items-center">
      <div class="bg-slate-50 p-3 border border-slate-200 rounded-lg w-80">
        <div v-for="n in blockExercises">
          <WodExercise @update-block="updateBlock" :exercises="exercises" :orderPosition="n.orderPosition" />
          <div class="w-full flex justify-center">
            <img src="/icons/connection.svg" alt="connextion" class="h-10">
          </div>
        </div>
        <div class="bg-white p-1 border border-slate-200 rounded-lg">
          <PrimaryButton @click="addExercise()" name="Ajouter un exercice" class="w-full" />
        </div>
      </div>
      <img src="/icons/connection.svg" alt="connextion" class="h-10">
    </div>
    
    <img src="/icons/horizontal-connection.svg" alt="connextion" class="w-10 mb-8">

    <div class="bg-slate-50 p-2 border border-slate-200 rounded-lg flex flex-col mb-8">
      <button type="button" @click="toggleBlockTime" id="wod-time-button" :class="{ 'hidden': showBlockTime }" class="w-10 h-10 rounded-lg bg-white p-2 text-gray-600 shadow-sm hover:bg-gray-100 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 border border-slate-200">
        <ClockIcon class="h-6 w-6" aria-hidden="true" />
      </button>
      <input @change="updateBlock" v-model="blockTime" type="number" name="wod-time" id="wod-time" :class="{ 'hidden': !showBlockTime }" class="mt-2 w-24 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6" placeholder="15 min" />
      <button type="button" @click="toggleRounds" id="rounds-button" :class="{ 'hidden': showRounds }" class="w-10 h-10 mt-2 rounded-lg bg-white p-2 text-gray-600 shadow-sm hover:bg-gray-100 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 border border-slate-200">
        <ArrowPathIcon class="h-6 w-6" aria-hidden="true" />
      </button>
      <input @change="updateBlock" v-model="rounds" type="number" name="rounds" id="rounds" :class="{ 'hidden': !showRounds }" class="mt-2 w-24 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6" placeholder="5 tours" />
    </div>
  </div>
  <div v-else>
    <div class="flex flex-col items-center">
      <div class="bg-slate-50 p-2 border border-slate-200 rounded-lg w-80">
        <input @change="updateBlock" v-model="blockTime" type="number" name="wod-break" id="wod-break" class="w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6" placeholder="5 min" />
      </div>
      <img src="/icons/connection.svg" alt="connextion" class="h-10">
    </div>
  </div>
</template>

<script setup>
import { ClockIcon } from '@heroicons/vue/20/solid'
import { ArrowPathIcon } from '@heroicons/vue/20/solid'

const { exercises, block } = defineProps(['exercises', 'block'])

const emit = defineEmits(['updateWod'])

const showBlockTime = ref(false)
const showRounds = ref(false)

let blockTime = defineModel('blockTime')
let rounds = defineModel('rounds')


function toggleBlockTime() {
  showBlockTime.value = !showBlockTime.value;
}

function toggleRounds() {
  showRounds.value = !showRounds.value;
}

let blockExercises = ref([
  {
    exercise: null,
    weight: null,
    rehearsals: null,
    time: null,
    advise: null,
    orderPosition: 0,
  }
]);

function addExercise() {
  let newExercise = {
    exercise: null,
    weight: null,
    rehearsals: null,
    time: null,
    advise: null,
    orderPosition: blockExercises.value.slice(-1)[0].orderPosition + 1
  };
  blockExercises.value.push(newExercise)
}

function updateBlock(data) {
  if(data.exercise) {
    updateObject(blockExercises.value.find((element) => element.orderPosition === data.orderPosition), data)
  }
  let updatedBlockExercises = block.break ? [] : blockExercises.value;
  emit('updateWod', {
    parentBlock: null,
    rehearsals: rounds.value,
    time: blockTime.value,
    break: block.break,
    childBlocks:[],
    blockExercises: updatedBlockExercises,
    blockResults: [],
    orderPosition: block.orderPosition
  })
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