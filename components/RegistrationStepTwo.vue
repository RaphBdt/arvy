<template>
    <div class="lg:w-1/2 w-full">
        <div v-if="error != null" class="rounded-md bg-red-50 p-4 mb-6">
            <div class="flex">
            <div class="flex-shrink-0">
                <svg class="h-5 w-5 text-red-400" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.28 7.22a.75.75 0 00-1.06 1.06L8.94 10l-1.72 1.72a.75.75 0 101.06 1.06L10 11.06l1.72 1.72a.75.75 0 101.06-1.06L11.06 10l1.72-1.72a.75.75 0 00-1.06-1.06L10 8.94 8.28 7.22z" clip-rule="evenodd" />
                </svg>
            </div>
            <div class="ml-3">
                <h3 class="text-sm font-medium text-red-800">{{ error }}</h3>
            </div>
            </div>
        </div>

        <h1 class="text-center text-xl mb-6">Vos informations</h1>

        <div class="border-b border-gray-900/10 pb-12">
            <div class="mt-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
                <div class="sm:col-span-3">
                    <label for="first-name" class="block text-sm font-medium leading-6 text-gray-900">Prénom</label>
                    <div class="mt-2">
                        <input v-model="firstName" type="text" name="first-name" id="first-name" autocomplete="given-name" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="sm:col-span-3">
                    <label for="last-name" class="block text-sm font-medium leading-6 text-gray-900">Nom</label>
                    <div class="mt-2">
                        <input v-model="lastName" type="text" name="last-name" id="last-name" autocomplete="family-name" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="email" class="block text-sm font-medium leading-6 text-gray-900">Adresse email</label>
                    <div class="mt-2">
                        <input v-model="email" id="email" name="email" type="email" autocomplete="email" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="username" class="block text-sm font-medium leading-6 text-gray-900">Nom d'utilisateur</label>
                    <div class="mt-2">
                        <input v-model="username" id="username" name="username" type="text" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="tel" class="block text-sm font-medium leading-6 text-gray-900">Téléphone</label>
                    <div class="mt-2">
                        <input id="tel" name="tel" type="tel" autocomplete="tel" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Mot de passe</label>
                    <div class="mt-2">
                        <input v-model="password" id="password" name="password" type="password" autocomplete="password" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>
            </div>
        </div>
        <PrimaryButton @click="clickBtnNext" class="mt-10" name="Continuer" />
    </div>
</template>

<script setup>
    const emit = defineEmits(['changeStepEvent'])

    const email = defineModel('email')
    const username = defineModel('username')
    const firstName = defineModel('firstName')
    const lastName = defineModel('lastName')
    const password = defineModel('password')

    let error = ref(null)

    async function clickBtnNext() {
        try {
            const { data: responseData } = await useFetch('https://main-bvxea6i-axul4nh3q5odm.fr-3.platformsh.site/api/register', {
                method: 'post',
                headers: {
                    "Content-Type": "application/json",
                },
                body: { 
                    "email": email,
                    "username": username,
                    "firstName": firstName,
                    "lastName": lastName,
                    "password": password
                }
            })

            console.log(responseData.value);
            if (responseData && responseData.value && responseData.value.id) {
                error.value = null
                emit('changeStepEvent')
            } else {
                error.value = "Erreur lors de l'inscription."
            }

        } catch (error) {
            error.value = "Erreur lors de l'inscription."
        }
    }
</script>

<style scoped>

</style>