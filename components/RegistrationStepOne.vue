<template>
    <div class="lg:w-1/2 w-full">
        <h1 class="text-center text-xl mb-6">Type de compte</h1>
        <fieldset>
            <legend class="sr-only">Server size</legend>
            <div class="space-y-4">
                <!-- Active: "border-violet-600 ring-2 ring-violet-600", Not Active: "border-gray-300" -->
                <label class="relative block cursor-pointer rounded-lg border bg-white px-6 py-4 shadow-sm focus:outline-none sm:flex sm:justify-between hover:border-violet-600 hover:ring-2 hover:ring-violet-600">
                <input type="radio" name="server-size" value="Hobby" class="sr-only" aria-labelledby="server-size-0-label" aria-describedby="server-size-0-description-0 server-size-0-description-1">
                <span class="flex items-center">
                    <span class="flex flex-col text-sm">
                    <span id="server-size-0-label" class="font-medium text-gray-900">Je suis un athlète</span>
                    <span id="server-size-0-description-0" class="text-gray-500">
                        <span class="block sm:inline">Je fais du CrossFit dans une box ou en loisir</span>
                    </span>
                    </span>
                </span>
                <!--
                    Active: "border", Not Active: "border-2"
                    Checked: "border-violet-600", Not Checked: "border-transparent"
                -->
                <span class="pointer-events-none absolute -inset-px rounded-lg border-2" aria-hidden="true"></span>
                </label>
                <!-- Active: "border-violet-600 ring-2 ring-violet-600", Not Active: "border-gray-300" -->
                <label class="relative block cursor-pointer rounded-lg border bg-white px-6 py-4 shadow-sm focus:outline-none sm:flex sm:justify-between hover:border-violet-600 hover:ring-2 hover:ring-violet-600">
                <input type="radio" name="server-size" value="Startup" class="sr-only" aria-labelledby="server-size-1-label" aria-describedby="server-size-1-description-0 server-size-1-description-1">
                <span class="flex items-center">
                    <span class="flex flex-col text-sm">
                    <span id="server-size-1-label" class="font-medium text-gray-900">Je suis gérant de box</span>
                    <span id="server-size-1-description-0" class="text-gray-500">
                        <span class="block sm:inline">Je suis le patron d'une box de CrossFit affiliée</span>
                    </span>
                    </span>
                </span>
                <!--
                    Active: "border", Not Active: "border-2"
                    Checked: "border-violet-600", Not Checked: "border-transparent"
                -->
                <span class="pointer-events-none absolute -inset-px rounded-lg border-2" aria-hidden="true"></span>
                </label>
            </div>
        </fieldset>
    </div>
</template>

<script setup>

</script>

<style scoped>

</style>