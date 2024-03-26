<template>
    <div>
        <div class="bg-gray-900">
            <header class="absolute inset-x-0 top-0 z-50">
                <nav class="flex items-center justify-between p-6 lg:px-8" aria-label="Global">
                    <div class="flex lg:flex-1">
                        <NuxtLink to="/" class="-m-1.5 p-1.5">
                            <span class="sr-only">Arvy</span>
                            <img class="h-8 w-auto" src="/arvy-logo.png" alt="">
                        </NuxtLink>
                    </div>
                    <div class="flex lg:hidden">
                        <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-400" @click="mobileMenuOpen = true">
                            <span class="sr-only">Ouvrir le menu principal</span>
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
                            </svg>
                        </button>
                    </div>
                    <!--<div class="hidden lg:flex lg:gap-x-12">
                        <NuxtLink to="/" class="text-sm font-semibold leading-6 text-white">Accueil</NuxtLink>
                        <a href="#" class="text-sm font-semibold leading-6 text-white">Le projet</a>
                        <a href="#" class="text-sm font-semibold leading-6 text-white">Roadmap</a>
                    </div>-->
                    <div class="hidden lg:flex lg:flex-1 lg:justify-end">
                        <NuxtLink to="/connexion" class="text-sm font-semibold leading-6 text-white">Connexion <span aria-hidden="true">&rarr;</span></NuxtLink>
                    </div>
                </nav>
                <!-- Mobile menu, show/hide based on menu open state. -->
                <div class="lg:hidden" role="dialog" aria-modal="true" v-if="mobileMenuOpen == true">
                <!-- Background backdrop, show/hide based on slide-over state. -->
                    <div class="fixed inset-0 z-50"></div>
                    <div class="fixed inset-y-0 right-0 z-50 w-full overflow-y-auto bg-gray-900 px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-white/10">
                        <div class="flex items-center justify-between">
                            <NuxtLink to="/" class="-m-1.5 p-1.5">
                                <span class="sr-only">Arvy</span>
                                <img class="h-8 w-auto" src="/arvy-logo.png" alt="">
                            </NuxtLink>
                            <button type="button" class="-m-2.5 rounded-md p-2.5 text-gray-400" @click="mobileMenuOpen = false">
                                <span class="sr-only">Fermer le menu</span>
                                <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                                </svg>
                            </button>
                        </div>
                        <div class="mt-6 flow-root">
                            <div class="-my-6 divide-y divide-gray-500/25">
                                <div class="space-y-2 py-6">
                                    <!--
                                    <NuxtLink to="/" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-white hover:bg-gray-800">Accueil</NuxtLink>
                                    <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-white hover:bg-gray-800">Le projet</a>
                                    <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-white hover:bg-gray-800">Roadmap</a>-->
                                </div>
                            </div>
                            <div class="py-6">
                                <NuxtLink to="/connexion" class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-white hover:bg-gray-800">Connexion</NuxtLink>
                            </div>
                        </div>
                    </div>
                </div>
            </header>

            <div class="relative isolate overflow-hidden pt-14 min-h-screen">
                <img src="/img/background-landing.jpg" alt="" class="absolute inset-0 -z-10 min-h-full w-full object-cover">
                <div class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80" aria-hidden="true">
                    <div class="relative left-[calc(50%-11rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 rotate-[30deg] bg-gradient-to-tr from-[#ff80b5] to-[#9089fc] opacity-20 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)"></div>
                </div>
                <div class="mx-auto max-w-2xl py-32 sm:py-48 lg:py-56">
                    <div class="hidden sm:mb-8 sm:flex sm:justify-center">
                        <div class="relative rounded-full px-3 py-1 text-sm leading-6 text-gray-400 ring-1 ring-white/10 hover:ring-white/20">
                            Projet en phase de réflexion / développement. <NuxtLink to="mailto:hello@arvy.app" class="font-semibold text-white"><span class="absolute inset-0" aria-hidden="true"></span>Rejoignez l'aventure <span aria-hidden="true">&rarr;</span></NuxtLink>
                        </div>
                    </div>
                    <div class="text-center">
                        <h1 class="text-4xl font-bold tracking-tight text-white sm:text-6xl">Enfin une app à la hauteur de vos performances</h1>
                        <p class="mt-6 text-lg leading-8 text-gray-300">Créez des modèles de WOD, enregistrez vos performances, partagez vos résultats et décrochez des trophées. Bienvenue sur votre nouvelle application de CrossFit tout-en-un. Conçue aussi bien pour les athlètes que pour les gérants de box.</p>
                        <div class="mt-10 flex items-center justify-center gap-x-6">
                            <AppButton name="Inscription" color="violet" link="/inscription" />
                            <NuxtLink to="/connexion" class="text-sm font-semibold leading-6 text-white">Connexion <span aria-hidden="true">→</span></NuxtLink>
                        </div>
                    </div>
                </div>
                <div class="absolute inset-x-0 top-[calc(100%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(100%-30rem)]" aria-hidden="true">
                    <div class="relative left-[calc(50%+3rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 bg-gradient-to-tr from-[#ff80b5] to-[#9089fc] opacity-20 sm:left-[calc(50%+36rem)] sm:w-[72.1875rem]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    const mobileMenuOpen = ref(false);

    useHead({
        title: 'Arvy | Votre meilleur partenaire CrossFit'
    })
</script>

<style scoped>

</style>