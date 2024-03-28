<template>
    <div class="bg-white rounded-lg border border-slate-200 w-80 p-1 flex justify-center items-center">
        <button @click="$emit('addBreakBlock')" type="button" class="mr-1 flex justify-center rounded-md bg-slate-200 px-3 py-1.5 text-sm font-semibold leading-6 shadow-sm hover:bg-slate-300 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-slate-300 w-1/3">Pause</button>
        <PrimaryButton @click="$emit('addExercisesBlock')" name="Ajouter un block" class="ml-1 w-2/3" />
    </div>
</template>

<script setup>
const emit = defineEmits(['addExercisesBlock', 'addBreakBlock'])
</script>

<style lang="scss" scoped>

</style>