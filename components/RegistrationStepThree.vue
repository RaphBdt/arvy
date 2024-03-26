<template>
    <div>
        <div v-if="errorMessage">
            <Alert :message="errorMessage" type="error" />
        </div>

        <RegistrationStepTitle title="Votre box" description="Entrez les informations de votre box" />
        
        <div class="pb-6">
            <div class="grid grid-cols-1 gap-x-6 gap-y-4 sm:grid-cols-6">
                <div class="col-span-full">
                    <label for="photo" class="block text-sm font-medium leading-6 text-gray-900">Logo</label>
                    <div class="mt-2 flex items-center gap-x-3">
                        <svg class="h-12 w-12 text-gray-300" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
                        <path fill-rule="evenodd" d="M18.685 19.097A9.723 9.723 0 0021.75 12c0-5.385-4.365-9.75-9.75-9.75S2.25 6.615 2.25 12a9.723 9.723 0 003.065 7.097A9.716 9.716 0 0012 21.75a9.716 9.716 0 006.685-2.653zm-12.54-1.285A7.486 7.486 0 0112 15a7.486 7.486 0 015.855 2.812A8.224 8.224 0 0112 20.25a8.224 8.224 0 01-5.855-2.438zM15.75 9a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0z" clip-rule="evenodd" />
                        </svg>
                        <button type="button" class="rounded-md bg-white px-2.5 py-1.5 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50">Change</button>
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="box-name" class="block text-sm font-medium leading-6 text-gray-900">Nom de la box*</label>
                    <div class="mt-2">
                        <input type="text" v-model="nameOfTheBox" name="box-name" id="box-name" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="street-address" class="block text-sm font-medium leading-6 text-gray-900">Adresse</label>
                    <div class="mt-2">
                        <input type="text" name="street-address" id="street-address" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="sm:col-span-3 sm:col-start-1">
                    <label for="city" class="block text-sm font-medium leading-6 text-gray-900">Ville</label>
                    <div class="mt-2">
                        <input type="text" name="city" id="city" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="sm:col-span-3">
                    <label for="postal-code" class="block text-sm font-medium leading-6 text-gray-900">Code postal</label>
                    <div class="mt-2">
                        <input type="text" name="postal-code" id="postal-code" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                    </div>
                </div>
            </div>
        </div>

        <AppButton @click="clickBtnNext" color="violet" class="w-full" name="Continuer" />
    </div>
</template>

<script setup>
const emit = defineEmits(['changeStepEvent', 'updateRegistrationEvent'])

const nameOfTheBox = defineModel('nameOfTheBox')

let errorMessage = ref(null)

function clickBtnNext() {
    if (nameOfTheBox.value) {
        emit('updateRegistrationEvent', {nameOfTheBox: nameOfTheBox.value})
        emit('changeStepEvent')
    } else {
        errorMessage.value = "Merci de remplir tous les champs obligatoires."
    }
}
</script>

<style lang="scss" scoped>

</style>