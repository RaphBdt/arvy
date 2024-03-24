<template>
    <div>
        <RegistrationHeader />
        <div class="mx-auto max-w-7xl px-6 lg:px-8">
            <RegistrationNav :steps="steps" />

            <div class="flex justify-center items-center my-14 lg:my-20">
                <div class="lg:w-96">
                    <RegistrationStepOne @change-step-event="changeStep" v-if="currentStep == 0" />
                    <RegistrationStepTwo @change-step-event="changeStep" v-else-if="currentStep == 1" />
                    <RegistrationStepThree @change-step-event="changeStep" v-else-if="currentStep == 2" />
                    <RegistrationStepFour v-else-if="currentStep == 3" />
                </div>
            </div>
        </div>
        <RegistrationFooter class="sticky bottom-0" />
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

async function changeStep() {
    steps.value[currentStep.value].status = "complete";
    currentStep.value = currentStep.value + 1;
    steps.value[currentStep.value].status = "current";

    // Temporary code
    if (currentStep.value == 3) {
        await navigateTo('/tableau-de-bord');
    }
}
</script>

<style scoped></style>