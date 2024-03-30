<template>
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto">
          <h1 class="text-base font-semibold leading-6 text-gray-900">Adhérents</h1>
        </div>
        <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
          <button type="button" class="block rounded-md bg-violet-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-violet-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-violet-600">Ajouter un adhérent</button>
        </div>
      </div>
      <div class="mt-8 flow-root">
        <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
            <table class="min-w-full divide-y divide-gray-300">
              <thead>
                <tr>
                  <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0">Nom</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Statut</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Type d'abonnement</th>
                  <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-0">
                    <span class="sr-only">Modifier</span>
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200 bg-white">
                <tr v-for="person in people" :key="person.email">
                  <td class="whitespace-nowrap py-5 pl-4 pr-3 text-sm sm:pl-0">
                    <div class="flex items-center">
                      <div>
                        <div class="font-medium text-gray-900">{{ person.name }}</div>
                        <div class="mt-1 text-gray-500">{{ person.email }}</div>
                      </div>
                    </div>
                  </td>
                  <td class="whitespace-nowrap px-3 py-5 text-sm text-gray-500">
                    <span class="inline-flex items-center rounded-md bg-green-50 px-2 py-1 text-xs font-medium text-green-700 ring-1 ring-inset ring-green-600/20">Actif</span>
                  </td>
                  <td class="whitespace-nowrap px-3 py-5 text-sm text-gray-500">{{ person.role }}</td>
                  <td class="relative whitespace-nowrap py-5 pl-3 pr-4 text-right text-sm font-medium sm:pr-0">
                    <a href="#" class="text-violet-600 hover:text-violet-900"
                      >Modifier<span class="sr-only">, {{ person.name }}</span></a
                    >
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  const people = [
    {
      name: 'Éléonore Dubois',
      email: 'eleonore.dubois@gmail.com',
      role: 'Adhérent annuel',
    },
    {
      name: 'Lucas Moreau',
      email: 'lucas.moreau@gmail.com',
      role: 'Adhérent annuel',
    },
    {
      name: 'Camille Lefevre',
      email: 'camille.lefevre@gmail.com',
      role: 'Adhérent annuel club Gym',
    },
    {
      name: 'Mathis Martin',
      email: 'mathis.martin@gmail.com',
      role: 'Adhérent mensuel',
    },
    {
      name: 'Léa Roussel',
      email: 'lea.roussel@gmail.com',
      role: 'Adhérent annuel',
    },
    {
      name: 'Gabriel Laurent',
      email: 'gabriel.laurent@gmail.com',
      role: 'Adhérent mensuel',
    },
    {
      name: 'Manon Girard',
      email: 'manon.girard@gmail.com',
      role: 'Adhérent mensuel',
    },    
    {
      name: 'Hugo Dupont',
      email: 'hugo.dupont@gmail.com',
      role: 'Adhérent mensuel',
    },
    {
      name: 'Clara Bernard',
      email: 'clara.bernard@gmail.com',
      role: 'Adhérent annuel',
    }
  ]

definePageMeta({
    layout: 'dashboard'
})
</script>