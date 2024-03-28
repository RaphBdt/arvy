<template>
    <div class="border-b border-gray-200 mb-10 pb-5 sm:flex sm:items-center sm:justify-between">
      <h3 class="text-base font-semibold leading-6 text-gray-900">Gestion des WODs</h3>
      <div class="mt-3 sm:ml-4 sm:mt-0">
        <PrimaryButton name="Accéder au créateur de WOD" link="/createur-de-wod" />
      </div>
    </div>
    <div>
    <ul v-if="wods" role="list" class="mt-3 grid grid-cols-1 gap-5 sm:grid-cols-2 sm:gap-6 lg:grid-cols-4">
      <li v-for="wodId in wods" class="col-span-1 flex rounded-md shadow-sm">
        <div class="bg-violet-500 flex w-16 py-5 flex-shrink-0 items-center justify-center rounded-l-md text-sm font-medium text-white">#{{ wodId }}</div>
        <div class="flex flex-1 items-center justify-between truncate rounded-r-md border-b border-r border-t border-gray-200 bg-white">
          <div class="flex-1 truncate px-4 py-2 text-sm">
            <NuxtLink :to="`/wods/${wodId}`" class="font-medium text-gray-900 hover:text-gray-600">WOD #{{ wodId }}</NuxtLink>
          </div>
          <div class="flex-shrink-0 pr-2">
            <button type="button" class="inline-flex h-8 w-8 items-center justify-center rounded-full bg-transparent bg-white text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
              <span class="sr-only">Open options</span>
              <EllipsisVerticalIcon class="h-5 w-5" aria-hidden="true" />
            </button>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>
  

<script setup>
import { EllipsisVerticalIcon } from '@heroicons/vue/20/solid'

let wods = ref([]);

definePageMeta({
    layout: 'dashboard'
})

let token = localStorage.getItem("token");
if (token != null) {
    useFetch('https://developpe-klnc5za-axul4nh3q5odm.fr-3.platformsh.site/api/wod', {
        method: 'get',
        headers: {
            "Authorization": `Bearer ${token}`,
        },
        onResponse({ response }) {
            if(response.status === 200) {
                wods.value = response._data.wods.map(item => item.id);
                wods.value.reverse()
            }
        }
    })
}
</script>

<style lang="scss" scoped>

</style>