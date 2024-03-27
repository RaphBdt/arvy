<template>
    <div class="bg-slate-100 p-4 border border-slate-200 rounded-lg">
        <WodExercise :exercises="exercises" />
        <div class="w-full flex justify-center">
          <img src="/icons/connection.svg" alt="connextion" class="h-10">
        </div>
        <div class="bg-white p-1 border border-slate-200 rounded-lg">
          <AppButton name="Ajouter un exercice" color="violet" class="w-full" />
        </div>
    </div>
</template>

<script setup>
const { exercises } = defineProps(["exercises"])
</script>

<style scoped>

</style>