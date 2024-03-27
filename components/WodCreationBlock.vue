<template>
    <div class="flex items-center">
      <div class="bg-slate-100 p-4 border border-slate-200 rounded-lg">
          <div v-for="n in numberOfExercise">
            <WodExercise :exercises="exercises" />
            <div class="w-full flex justify-center">
              <img src="/icons/connection.svg" alt="connextion" class="h-10">
            </div>
          </div>
          <div class="bg-white p-1 border border-slate-200 rounded-lg">
            <AppButton @click="addExercise()" name="Ajouter un exercice" color="violet" class="w-full" />
          </div>
      </div>

      <img src="/icons/horizontal-connection.svg" alt="connextion" class="w-10">

      <div class="bg-slate-100 p-2 border border-slate-200 rounded-lg flex flex-col">
        <button type="button" @click="toggleWodTime" id="wod-time-button" :class="{ 'hidden': showWodTime }" class="w-10 h-10 rounded-lg bg-white p-2 text-gray-600 shadow-sm hover:bg-gray-100 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 border border-slate-200">
          <ClockIcon class="h-6 w-6" aria-hidden="true" />
        </button>
        <input type="number" name="wod-time" id="wod-time" :class="{ 'hidden': !showWodTime }" class="mt-2 w-24 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6" placeholder="15 min" />
        <button type="button" @click="toggleRounds" id="rounds-button" :class="{ 'hidden': showRounds }" class="w-10 h-10 mt-2 rounded-lg bg-white p-2 text-gray-600 shadow-sm hover:bg-gray-100 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 border border-slate-200">
          <ArrowPathIcon class="h-6 w-6" aria-hidden="true" />
        </button>
        <input type="number" name="rounds" id="rounds" :class="{ 'hidden': !showRounds }" class="mt-2 w-24 rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6" placeholder="5 tours" />
      </div>
    </div>
</template>

<script setup>
import { ClockIcon } from '@heroicons/vue/20/solid'
import { ArrowPathIcon } from '@heroicons/vue/20/solid'

const { exercises } = defineProps(["exercises"])

const showWodTime = ref(false)
const showRounds = ref(false)

let numberOfExercise = ref(1);

function toggleWodTime() {
  showWodTime.value = !showWodTime.value;
}
function toggleRounds() {
  showRounds.value = !showRounds.value;
}

function addExercise() {
  numberOfExercise.value++;
}
</script>

<style scoped>

</style>