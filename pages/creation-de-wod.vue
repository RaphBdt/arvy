<template>
    <div class="min-h-[83vh] w-full border-solid border border-gray rounded-lg background-custom-repeted-points flex flex-col items-center">
        <div>
            <button type="button" class="rounded-md bg-white px-3 py-2 text-sm font-semibold shadow-sm ring-1 ring-inset ring-gray-300 uppercase text-lime-500 mt-10">Start</button>
        </div>
        <WodCreationBlock />
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'dashboard'
})
</script>

<style scoped>
    .background-custom-repeted-points {
        --dot-bg: white;
        --dot-color: gray;
        --dot-size: 1px;
        --dot-space: 12px;
            background:
                linear-gradient(90deg, var(--dot-bg) calc(var(--dot-space) - var(--dot-size)), transparent 1%) center / var(--dot-space) var(--dot-space),
                linear-gradient(var(--dot-bg) calc(var(--dot-space) - var(--dot-size)), transparent 1%) center / var(--dot-space) var(--dot-space),
                var(--dot-color);
    } 
</style>