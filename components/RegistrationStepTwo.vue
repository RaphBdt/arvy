<template>
    <div>
        <div v-if="errorMessage">
            <Alert :message="errorMessage" type="error" />
        </div>

        <RegistrationStepTitle title="Vos informations" description="Inscrivez-vous sur Arvy !" />

        <div class="pb-6">
            <div class="grid grid-cols-1 gap-x-6 gap-y-4 sm:grid-cols-6">
                <div class="sm:col-span-3">
                    <label for="first-name" class="block text-sm font-medium leading-6 text-gray-900">Prénom*</label>
                    <div class="mt-2">
                        <input v-model="firstName" type="text" name="first-name" id="first-name"
                            autocomplete="given-name"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="sm:col-span-3">
                    <label for="last-name" class="block text-sm font-medium leading-6 text-gray-900">Nom*</label>
                    <div class="mt-2">
                        <input v-model="lastName" type="text" name="last-name" id="last-name" autocomplete="family-name"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="email" class="block text-sm font-medium leading-6 text-gray-900">Adresse email*</label>
                    <div class="mt-2">
                        <input v-model="email" id="email" name="email" type="email" autocomplete="email"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="username" class="block text-sm font-medium leading-6 text-gray-900">Nom
                        d'utilisateur*</label>
                    <div class="mt-2">
                        <input v-model="username" id="username" name="username" type="text"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>

                <div class="col-span-full">
                    <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Mot de passe*</label>
                    <div class="mt-2">
                        <input v-model="password" id="password" name="password" type="password" autocomplete="password"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6">
                    </div>
                </div>
            </div>
        </div>
        <Button @click="clickBtnNext" color="violet" title="Continuer" class="w-full" name="Continuer" />
    </div>
</template>

<script setup>
const emit = defineEmits(['changeStepEvent', 'updateRegistrationEvent'])

const email = defineModel('email')
const username = defineModel('username')
const firstName = defineModel('firstName')
const lastName = defineModel('lastName')
const password = defineModel('password')

let errorMessage = ref(null)

async function clickBtnNext() {
    if (email.value && username.value && firstName.value && lastName.value && password.value) {
        const user = {
            "email": email.value,
            "username": username.value,
            "firstName": firstName.value,
            "lastName": lastName.value,
            "password": password.value
        }

        await useFetch('https://main-bvxea6i-axul4nh3q5odm.fr-3.platformsh.site/api/register', {
            method: 'post',
            headers: {
                "Content-Type": "application/json",
            },
            body: user,
            onResponse({ response }) {
                if (response.status === 200) {
                    errorMessage.value = null
                    emit('updateRegistrationEvent', user)
                    emit('changeStepEvent')
                } else {
                    errorMessage.value = "Erreur lors de l'inscription. Votre nom d'utilisateur et votre adresse mail doivent être uniques sur l'application."
                }
            }
        })
    } else {
        errorMessage.value = "Merci de remplir tous les champs obligatoires."
    }
}
</script>

<style scoped></style>