<template>
    <div class="bg-white p-2 rounded-lg border border-slate-200 w-full">
        <Combobox class="w-full" as="div" v-model="selectedExercise">
            <div class="relative">
                <ComboboxInput
                    class="w-full rounded-md border-0 bg-white py-1.5 pl-3 pr-10 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6"
                    @change="query = $event.target.value" :display-value="(exercise) => exercise?.name" />
                <ComboboxButton class="absolute inset-y-0 right-0 flex items-center rounded-r-md px-2 focus:outline-none">
                    <ChevronUpDownIcon class="h-5 w-5 text-gray-400" aria-hidden="true" />
                </ComboboxButton>
    
                <ComboboxOptions v-if="filteredExercises.length > 0"
                    class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none sm:text-sm">
                    <ComboboxOption v-for="exercise in filteredExercises" :key="exercise.id" :value="exercise" as="template"
                        v-slot="{ active, selected }">
                        <li
                            :class="['relative cursor-default select-none py-2 pl-3 pr-9', active ? 'bg-violet-600 text-white' : 'text-gray-900']">
                            <span :class="['block truncate', selected && 'font-semibold']">
                                {{ exercise.name }}
                            </span>
    
                            <span v-if="selected"
                                :class="['absolute inset-y-0 right-0 flex items-center pr-4', active ? 'text-white' : 'text-violet-600']">
                                <CheckIcon class="h-5 w-5" aria-hidden="true" />
                            </span>
                        </li>
                    </ComboboxOption>
                </ComboboxOptions>
            </div>
        </Combobox>
        <div class="flex w-full">
            <div class="mt-2 w-1/2 mr-1">
                <input @change="updateExercise" v-model="reps" type="number" name="reps" id="reps"
                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6"
                    placeholder="10 Réps'" />
            </div>
            <div class="mt-2 w-1/2 ml-1">
                <input @change="updateExercise" v-model="weight" type="number" name="weight" id="weight"
                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6"
                    placeholder="Poids" />
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed, ref } from 'vue'
import { CheckIcon, ChevronUpDownIcon } from '@heroicons/vue/20/solid'
import {
    Combobox,
    ComboboxButton,
    ComboboxInput,
    ComboboxLabel,
    ComboboxOption,
    ComboboxOptions,
} from '@headlessui/vue'

const { exercises, blockExercise } = defineProps(["exercises", "blockExercise"])

const emit = defineEmits(['updateBlock'])

const exercisesGoodFormat = exercises.map(({ id, name }) => ({ id, name }));

const query = ref('')

const selectedExercise = ref()
watch(selectedExercise, () => {
    updateExercise()
})

const filteredExercises = computed(() =>
    query.value === ''
        ? exercisesGoodFormat
        : exercisesGoodFormat.filter((exercise) => {
            return exercise.name.toLowerCase().includes(query.value.toLowerCase())
        })
)

let reps = defineModel('reps')
let weight = defineModel('weight')

if (blockExercise.exercise) {
    selectedExercise.value = blockExercise.exercise
    reps.value = blockExercise.rehearsals
    weight.value = blockExercise.weight
}

function updateExercise() {
    if(selectedExercise.value) {
        emit('updateBlock', {
          exercise: selectedExercise.value.id,
          weight: weight.value,
          rehearsals: reps.value,
          time: null,
          advise: null,
          orderPosition: blockExercise.orderPosition,
        })
    }
}
</script>