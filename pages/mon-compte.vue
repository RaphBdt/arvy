<template>
    <div class="mx-auto max-w-7xl lg:flex lg:gap-x-16">
        <h1 class="sr-only">Réglages généraux</h1>

        <aside
            class="flex overflow-x-auto border-b border-gray-900/5 py-4 lg:block lg:w-64 lg:flex-none lg:border-0">
            <nav class="flex-none px-4 sm:px-6 lg:px-0">
                <ul role="list" class="flex gap-x-3 gap-y-1 whitespace-nowrap lg:flex-col">
                    <li v-for="item in secondaryNavigation" :key="item.name">
                        <a :href="item.href" @click="clickOnMenuPage(item.name)"
                            :class="[item.current ? 'bg-gray-50 text-violet-600' : 'text-gray-700 hover:text-violet-600 hover:bg-gray-50', 'group flex gap-x-3 rounded-md py-2 pl-2 pr-3 text-sm leading-6 font-semibold']">
                            <component :is="item.icon"
                                :class="[item.current ? 'text-violet-600' : 'text-gray-400 group-hover:text-violet-600', 'h-6 w-6 shrink-0']"
                                aria-hidden="true" />
                            {{ item.name }}
                        </a>
                    </li>
                </ul>
            </nav>
        </aside>

        <main class="px-4 py-4 sm:px-6 lg:flex-auto lg:px-0">
            <div class="mx-auto max-w-2xl space-y-16 sm:space-y-20 lg:mx-0 lg:max-w-none">
                <div>
                    <h2 class="text-base font-semibold leading-7 text-gray-900">Profil</h2>
                    <p class="mt-1 text-sm leading-6 text-gray-500">Ces informations sont affichées publiquement.</p>

                    <dl class="mt-6 space-y-6 divide-y divide-gray-100 border-t border-gray-200 text-sm leading-6">
                        <div class="pt-6 sm:flex">
                            <dt class="font-medium text-gray-900 sm:w-64 sm:flex-none sm:pr-6">Nom</dt>
                            <dd class="mt-1 flex justify-between gap-x-6 sm:mt-0 sm:flex-auto">
                                <div v-if="currentUser.firstName && currentUser.lastName" class="text-gray-900">{{ currentUser.firstName }} {{ currentUser.lastName }}</div>
                                <button type="button"
                                    class="font-semibold text-violet-600 hover:text-violet-500">Mise à jour</button>
                            </dd>
                        </div>
                        <div class="pt-6 sm:flex">
                            <dt class="font-medium text-gray-900 sm:w-64 sm:flex-none sm:pr-6">Adresse mail</dt>
                            <dd class="mt-1 flex justify-between gap-x-6 sm:mt-0 sm:flex-auto">
                                <div v-if="currentUser.email" class="text-gray-900">{{ currentUser.email }}</div>
                                <button type="button"
                                    class="font-semibold text-violet-600 hover:text-violet-500">Mise à jour</button>
                            </dd>
                        </div>
                        <div class="pt-6 sm:flex">
                            <dt class="font-medium text-gray-900 sm:w-64 sm:flex-none sm:pr-6">Titre</dt>
                            <dd class="mt-1 flex justify-between gap-x-6 sm:mt-0 sm:flex-auto">
                                <div class="text-gray-900">Gérant de box affiliée CrossFit</div>
                                <button type="button"
                                    class="font-semibold text-violet-600 hover:text-violet-500">Mise à jour</button>
                            </dd>
                        </div>
                    </dl>
                </div>

                <div>
                    <h2 class="text-base font-semibold leading-7 text-gray-900">Comptes bancaires liés</h2>
                    <p class="mt-1 text-sm leading-6 text-gray-500">Enregistrez vos compte professionnels pour transférer automatiquement votre argent reçu via Arvy.</p>

                    <ul role="list" class="mt-6 divide-y divide-gray-100 border-t border-gray-200 text-sm leading-6">
                        <li class="flex justify-between gap-x-6 py-6">
                            <div class="font-medium text-gray-900">CA des Savoie</div>
                            <button type="button"
                                class="font-semibold text-violet-600 hover:text-violet-500">Mise à jour</button>
                        </li>
                        <li class="flex justify-between gap-x-6 py-6">
                            <div class="font-medium text-gray-900">BNB Paribas</div>
                            <button type="button"
                                class="font-semibold text-violet-600 hover:text-violet-500">Mise à jour</button>
                        </li>
                    </ul>

                    <div class="flex border-t border-gray-100 pt-6">
                        <button type="button"
                            class="text-sm font-semibold leading-6 text-violet-600 hover:text-violet-500"><span
                                aria-hidden="true">+</span> Ajouter une nouvelle banque</button>
                    </div>
                </div>

                <div>
                    <h2 class="text-base font-semibold leading-7 text-gray-900">Applications externes</h2>
                    <p class="mt-1 text-sm leading-6 text-gray-500">Connectez d'autres applications pour avoir toujours plus de fonctionnalités 🚀</p>

                    <ul role="list" class="mt-6 divide-y divide-gray-100 border-t border-gray-200 text-sm leading-6">
                        <li class="flex justify-between gap-x-6 py-6">
                            <div class="font-medium text-gray-900">Google Calendar</div>
                            <button type="button"
                                class="font-semibold text-violet-600 hover:text-violet-500">Mise à jour</button>
                        </li>
                    </ul>

                    <div class="flex border-t border-gray-100 pt-6">
                        <button type="button"
                            class="text-sm font-semibold leading-6 text-violet-600 hover:text-violet-500"><span
                                aria-hidden="true">+</span> Ajouter une nouvelle application</button>
                    </div>
                </div>

                <div>
                    <h2 class="text-base font-semibold leading-7 text-gray-900">Formats</h2>
                    <p class="mt-1 text-sm leading-6 text-gray-500">Choisissez vos préférences en termes d'affichage.</p>

                    <dl class="mt-6 space-y-6 divide-y divide-gray-100 border-t border-gray-200 text-sm leading-6">
                        <div class="pt-6 sm:flex">
                            <dt class="font-medium text-gray-900 sm:w-64 sm:flex-none sm:pr-6">Langue</dt>
                            <dd class="mt-1 flex justify-between gap-x-6 sm:mt-0 sm:flex-auto">
                                <div class="text-gray-900">Anglais</div>
                                <button type="button"
                                    class="font-semibold text-violet-600 hover:text-violet-500">Mise à jour</button>
                            </dd>
                        </div>
                        <div class="pt-6 sm:flex">
                            <dt class="font-medium text-gray-900 sm:w-64 sm:flex-none sm:pr-6">Format de date</dt>
                            <dd class="mt-1 flex justify-between gap-x-6 sm:mt-0 sm:flex-auto">
                                <div class="text-gray-900">DD-MM-YYYY</div>
                                <button type="button"
                                    class="font-semibold text-violet-600 hover:text-violet-500">Mise à jour</button>
                            </dd>
                        </div>
                        <SwitchGroup as="div" class="flex pt-6">
                            <SwitchLabel as="dt" class="flex-none pr-6 font-medium text-gray-900 sm:w-64" passive>
                                Heure basée en fonction de votre localisation</SwitchLabel>
                            <dd class="flex flex-auto items-center justify-end">
                                <Switch v-model="automaticTimezoneEnabled"
                                    :class="[automaticTimezoneEnabled ? 'bg-violet-600' : 'bg-gray-200', 'flex w-8 cursor-pointer rounded-full p-px ring-1 ring-inset ring-gray-900/5 transition-colors duration-200 ease-in-out focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-violet-600']">
                                    <span aria-hidden="true"
                                        :class="[automaticTimezoneEnabled ? 'translate-x-3.5' : 'translate-x-0', 'h-4 w-4 transform rounded-full bg-white shadow-sm ring-1 ring-gray-900/5 transition duration-200 ease-in-out']" />
                                </Switch>
                            </dd>
                        </SwitchGroup>
                    </dl>
                </div>
            </div>
        </main>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import { Dialog, DialogPanel, Switch, SwitchGroup, SwitchLabel } from '@headlessui/vue'
import { Bars3Icon } from '@heroicons/vue/20/solid'
import {
    BellIcon,
    CreditCardIcon,
    CubeIcon,
    FingerPrintIcon,
    UserCircleIcon,
    UsersIcon,
    XMarkIcon,
    PowerIcon
} from '@heroicons/vue/24/outline'

definePageMeta({
    layout: 'dashboard'
})

const navigation = [
    { name: 'Home', href: '#' },
    { name: 'Invoices', href: '#' },
    { name: 'Clients', href: '#' },
    { name: 'Expenses', href: '#' },
]
const secondaryNavigation = [
    { name: 'Général', href: '#', icon: UserCircleIcon, current: true },
    { name: 'Sécurité', href: '#', icon: FingerPrintIcon, current: false },
    { name: 'Notifications', href: '#', icon: BellIcon, current: false },
    { name: 'Offres', href: '#', icon: CubeIcon, current: false },
    { name: 'Factures', href: '#', icon: CreditCardIcon, current: false },
    { name: 'Mon équipe', href: '#', icon: UsersIcon, current: false },
    { name: 'Déconnexion', href: '#', icon: PowerIcon, current: false },
]

const mobileMenuOpen = ref(false)
const automaticTimezoneEnabled = ref(true)

function clickOnMenuPage(itemName) {
    if (itemName === 'Déconnexion') {
        localStorage.removeItem('token');
        navigateTo('/connexion');
    }
}

let currentUser = ref({})

let token = localStorage.getItem("token");
if (token != null) {
    useFetch('https://developpe-klnc5za-axul4nh3q5odm.fr-3.platformsh.site/api/profile', {
        method: 'get',
        headers: {
            "Authorization": `Bearer ${token}`,
        },
        onResponse({ response }) {
            if(response.status === 200) {
                let userObject = {
                    firstName: response._data.firstName,
                    lastName: response._data.lastName,
                    email: response._data.email,
                }
                currentUser.value = userObject;
            }
        }
    })
} else {
    navigateTo('/connexion');
}
</script>