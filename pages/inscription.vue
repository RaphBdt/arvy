<template>
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <nav class="my-8 lg:my-10" aria-label="Progress">
            <ol role="list" class="divide-y divide-gray-300 rounded-md border border-gray-300 md:flex md:divide-y-0">
            <li v-for="(step, stepIdx) in steps" :key="step.name" class="relative md:flex md:flex-1">
                <a v-if="step.status === 'complete'" :href="step.href" class="group flex w-full items-center">
                <span class="flex items-center px-6 py-4 text-sm font-medium">
                    <span class="flex h-10 w-10 flex-shrink-0 items-center justify-center rounded-full bg-violet-600 group-hover:bg-violet-800">
                        <svg class="h-6 w-6 text-white" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
                            <path fill-rule="evenodd" d="M19.916 4.626a.75.75 0 01.208 1.04l-9 13.5a.75.75 0 01-1.154.114l-6-6a.75.75 0 011.06-1.06l5.353 5.353 8.493-12.739a.75.75 0 011.04-.208z" clip-rule="evenodd" />
                        </svg>
                    </span>
                    <span class="ml-4 text-sm font-medium text-gray-900">{{ step.name }}</span>
                </span>
                </a>
                <a v-else-if="step.status === 'current'" :href="step.href" class="flex items-center px-6 py-4 text-sm font-medium" aria-current="step">
                <span class="flex h-10 w-10 flex-shrink-0 items-center justify-center rounded-full border-2 border-violet-600">
                    <span class="text-violet-600">{{ step.id }}</span>
                </span>
                <span class="ml-4 text-sm font-medium text-violet-600">{{ step.name }}</span>
                </a>
                <a v-else :href="step.href" class="group flex items-center">
                <span class="flex items-center px-6 py-4 text-sm font-medium">
                    <span class="flex h-10 w-10 flex-shrink-0 items-center justify-center rounded-full border-2 border-gray-300 group-hover:border-gray-400">
                    <span class="text-gray-500 group-hover:text-gray-900">{{ step.id }}</span>
                    </span>
                    <span class="ml-4 text-sm font-medium text-gray-500 group-hover:text-gray-900">{{ step.name }}</span>
                </span>
                </a>
                <template v-if="stepIdx !== steps.length - 1">
                <!-- Arrow separator for lg screens and up -->
                <div class="absolute right-0 top-0 hidden h-full w-5 md:block" aria-hidden="true">
                    <svg class="h-full w-full text-gray-300" viewBox="0 0 22 80" fill="none" preserveAspectRatio="none">
                    <path d="M0 -2L20 40L0 82" vector-effect="non-scaling-stroke" stroke="currentcolor" stroke-linejoin="round" />
                    </svg>
                </div>
                </template>
            </li>
            </ol>
        </nav>

        <div class="flex justify-center items-center my-14 lg:my-28">
            <RegistrationStepOne @change-step-event="changeStep" v-if="currentStep == 0" />
            <RegistrationStepTwo @change-step-event="changeStep" v-else-if="currentStep == 1" />
            <RegistrationStepThree @change-step-event="changeStep" v-else-if="currentStep == 2" />
            <RegistrationStepFour v-else-if="currentStep == 3" />
        </div>
    </div>
</template>

<script setup>
    let steps = ref([
        { id: '01', name: 'Compte', href: '#', status: 'current' },
        { id: '02', name: 'Informations', href: '#', status: 'upcoming' },
        { id: '03', name: 'Box', href: '#', status: 'upcoming' },
        { id: '04', name: 'Résumé', href: '#', status: 'upcoming' },
    ])

    let currentStep = ref(0);

    function changeStep() {
        steps.value[currentStep.value].status = "complete";
        currentStep.value = currentStep.value + 1;
        steps.value[currentStep.value].status = "current";
    }
</script>

<style scoped>

</style>