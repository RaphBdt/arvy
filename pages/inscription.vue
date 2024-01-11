<template>
    <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
        <nav class="lg:my-10" aria-label="Progress">
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
    </div>

    <div class="mx-auto max-w-7xl sm:px-6 lg:px-8 flex justify-center items-center my-14 lg:my-32">
        <div class="w-full max-w-sm space-y-10" v-if="step == 1">
            <div>
                <img class="mx-auto h-10 w-auto" src="/arvy-logo.png" alt="Your Company">
                <h2 class="mt-10 text-center text-2xl font-bold leading-9 tracking-tight text-gray-900">Sign in to your account</h2>
            </div>
            <form class="space-y-6" action="#" method="POST">
            <div class="relative -space-y-px rounded-md shadow-sm">
                <div class="pointer-events-none absolute inset-0 z-10 rounded-md ring-1 ring-inset ring-gray-300"></div>
                <div>
                    <label for="email-address" class="sr-only">Email address</label>
                    <input id="email-address" name="email" type="email" autocomplete="email" required class="relative block w-full rounded-t-md border-0 py-1.5 text-gray-900 ring-1 ring-inset ring-gray-100 placeholder:text-gray-400 focus:z-10 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6" placeholder="Email address">
                </div>
                <div>
                    <label for="password" class="sr-only">Password</label>
                    <input id="password" name="password" type="password" autocomplete="current-password" required class="relative block w-full rounded-b-md border-0 py-1.5 text-gray-900 ring-1 ring-inset ring-gray-100 placeholder:text-gray-400 focus:z-10 focus:ring-2 focus:ring-inset focus:ring-violet-600 sm:text-sm sm:leading-6" placeholder="Password">
                </div>
            </div>
    
            <div class="flex items-center justify-between">
                <div class="flex items-center">
                <input id="remember-me" name="remember-me" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-violet-600 focus:ring-violet-600">
                <label for="remember-me" class="ml-3 block text-sm leading-6 text-gray-900">Remember me</label>
                </div>
    
                <div class="text-sm leading-6">
                <a href="#" class="font-semibold text-violet-600 hover:text-violet-500">Forgot password?</a>
                </div>
            </div>
    
            <div>
                <button type="submit" class="flex w-full justify-center rounded-md bg-violet-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white hover:bg-violet-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-violet-600">Sign in</button>
            </div>
            </form>
    
            <p class="text-center text-sm leading-6 text-gray-500">
            Not a member?
            <a href="#" class="font-semibold text-violet-600 hover:text-violet-500">Start a 14-day free trial</a>
            </p>
        </div>
    </div>
</template>

<script setup>
let steps = [
    { id: '01', name: 'Compte', href: '#', status: 'complete' },
    { id: '02', name: 'Informations', href: '#', status: 'current' },
    { id: '03', name: 'Box', href: '#', status: 'upcoming' },
    { id: '03', name: 'Sécurité', href: '#', status: 'upcoming' },
    { id: '03', name: 'Résumé', href: '#', status: 'upcoming' },
]

let currentStep = 0;
</script>

<style scoped>

</style>