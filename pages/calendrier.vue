<template>
<div class="flex h-full flex-col">
  <header class="flex flex-none items-center justify-between border-b border-gray-200 px-6 py-4">
    <h1 class="text-base font-semibold leading-6 text-gray-900">
      <time datetime="2022-01">Avril 2024</time>
    </h1>
    <div class="flex items-center">
      <div class="relative flex items-center rounded-md bg-white shadow-sm md:items-stretch">
        <button type="button" class="flex h-9 w-12 items-center justify-center rounded-l-md border-y border-l border-gray-300 pr-1 text-gray-400 hover:text-gray-500 focus:relative md:w-9 md:pr-0 md:hover:bg-gray-50">
          <span class="sr-only">Semaine précédente</span>
          <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
            <path fill-rule="evenodd" d="M12.79 5.23a.75.75 0 01-.02 1.06L8.832 10l3.938 3.71a.75.75 0 11-1.04 1.08l-4.5-4.25a.75.75 0 010-1.08l4.5-4.25a.75.75 0 011.06.02z" clip-rule="evenodd" />
          </svg>
        </button>
        <button type="button" class="hidden border-y border-gray-300 px-3.5 text-sm font-semibold text-gray-900 hover:bg-gray-50 focus:relative md:block">Aujourd'hui</button>
        <span class="relative -mx-px h-5 w-px bg-gray-300 md:hidden"></span>
        <button type="button" class="flex h-9 w-12 items-center justify-center rounded-r-md border-y border-r border-gray-300 pl-1 text-gray-400 hover:text-gray-500 focus:relative md:w-9 md:pl-0 md:hover:bg-gray-50">
          <span class="sr-only">Semaine suivante</span>
          <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
            <path fill-rule="evenodd" d="M7.21 14.77a.75.75 0 01.02-1.06L11.168 10 7.23 6.29a.75.75 0 111.04-1.08l4.5 4.25a.75.75 0 010 1.08l-4.5 4.25a.75.75 0 01-1.06-.02z" clip-rule="evenodd" />
          </svg>
        </button>
      </div>
      <div class="hidden md:ml-4 md:flex md:items-center">
        <div class="relative">
          <button type="button" class="flex items-center gap-x-1.5 rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50" id="menu-button" aria-expanded="false" aria-haspopup="true">
            Vue semaine
            <svg class="-mr-1 h-5 w-5 text-gray-400" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
              <path fill-rule="evenodd" d="M5.23 7.21a.75.75 0 011.06.02L10 11.168l3.71-3.938a.75.75 0 111.08 1.04l-4.25 4.5a.75.75 0 01-1.08 0l-4.25-4.5a.75.75 0 01.02-1.06z" clip-rule="evenodd" />
            </svg>
          </button>

          <!--
            Dropdown menu, show/hide based on menu state.

            Entering: "transition ease-out duration-100"
              From: "transform opacity-0 scale-95"
              To: "transform opacity-100 scale-100"
            Leaving: "transition ease-in duration-75"
              From: "transform opacity-100 scale-100"
              To: "transform opacity-0 scale-95"
          
          <div class="absolute right-0 z-10 mt-3 w-36 origin-top-right overflow-hidden rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none" role="menu" aria-orientation="vertical" aria-labelledby="menu-button" tabindex="-1">
            <div class="py-1" role="none">
              Active: "bg-gray-100 text-gray-900", Not Active: "text-gray-700" 
              <a href="#" class="text-gray-700 block px-4 py-2 text-sm" role="menuitem" tabindex="-1" id="menu-item-0">Day view</a>
              <a href="#" class="text-gray-700 block px-4 py-2 text-sm" role="menuitem" tabindex="-1" id="menu-item-1">Week view</a>
              <a href="#" class="text-gray-700 block px-4 py-2 text-sm" role="menuitem" tabindex="-1" id="menu-item-2">Month view</a>
              <a href="#" class="text-gray-700 block px-4 py-2 text-sm" role="menuitem" tabindex="-1" id="menu-item-3">Year view</a>
            </div>
          </div>
          -->
        </div>
        <div class="ml-6 h-6 w-px bg-gray-300"></div>
        <button type="button" class="ml-6 rounded-md bg-violet-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-violet-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-violet-500">Add event</button>
      </div>
      <div class="relative ml-6 md:hidden">
        <button type="button" class="-mx-2 flex items-center rounded-full border border-transparent p-2 text-gray-400 hover:text-gray-500" id="menu-0-button" aria-expanded="false" aria-haspopup="true">
          <span class="sr-only">Open menu</span>
          <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
            <path d="M3 10a1.5 1.5 0 113 0 1.5 1.5 0 01-3 0zM8.5 10a1.5 1.5 0 113 0 1.5 1.5 0 01-3 0zM15.5 8.5a1.5 1.5 0 100 3 1.5 1.5 0 000-3z" />
          </svg>
        </button>
      </div>
    </div>
  </header>
  <div class="isolate flex flex-auto flex-col overflow-auto bg-white">
    <div style="width: 165%" class="flex max-w-full flex-none flex-col sm:max-w-none md:max-w-full">
      <div class="sticky top-0 z-30 flex-none bg-white shadow ring-1 ring-black ring-opacity-5 sm:pr-8">
        <div class="grid grid-cols-7 text-sm leading-6 text-gray-500 sm:hidden">
          <button type="button" class="flex flex-col items-center pb-3 pt-2">M <span class="mt-1 flex h-8 w-8 items-center justify-center font-semibold text-gray-900">10</span></button>
          <button type="button" class="flex flex-col items-center pb-3 pt-2">T <span class="mt-1 flex h-8 w-8 items-center justify-center font-semibold text-gray-900">11</span></button>
          <button type="button" class="flex flex-col items-center pb-3 pt-2">W <span class="mt-1 flex h-8 w-8 items-center justify-center rounded-full bg-violet-600 font-semibold text-white">12</span></button>
          <button type="button" class="flex flex-col items-center pb-3 pt-2">T <span class="mt-1 flex h-8 w-8 items-center justify-center font-semibold text-gray-900">13</span></button>
          <button type="button" class="flex flex-col items-center pb-3 pt-2">F <span class="mt-1 flex h-8 w-8 items-center justify-center font-semibold text-gray-900">14</span></button>
          <button type="button" class="flex flex-col items-center pb-3 pt-2">S <span class="mt-1 flex h-8 w-8 items-center justify-center font-semibold text-gray-900">15</span></button>
          <button type="button" class="flex flex-col items-center pb-3 pt-2">S <span class="mt-1 flex h-8 w-8 items-center justify-center font-semibold text-gray-900">16</span></button>
        </div>

        <div class="-mr-px hidden grid-cols-7 divide-x divide-gray-100 border-r border-gray-100 text-sm leading-6 text-gray-500 sm:grid">
          <div class="col-end-1 w-14"></div>
          <div class="flex items-center justify-center py-3">
            <span>Lun <span class="items-center justify-center font-semibold text-gray-900">04</span></span>
          </div>
          <div class="flex items-center justify-center py-3">
            <span>Mar <span class="items-center justify-center font-semibold text-gray-900">05</span></span>
          </div>
          <div class="flex items-center justify-center py-3">
            <span>Jeu <span class="items-center justify-center font-semibold text-gray-900">06</span></span>
          </div>
          <div class="flex items-center justify-center py-3">
            <span>Jeu <span class="items-center justify-center font-semibold text-gray-900">07</span></span>
          </div>
          <div class="flex items-center justify-center py-3">
            <span class="flex items-baseline">Ven <span class="ml-1.5 flex h-8 w-8 items-center justify-center rounded-full bg-violet-600 font-semibold text-white">08</span></span>
          </div>
          <div class="flex items-center justify-center py-3">
            <span>Sam <span class="items-center justify-center font-semibold text-gray-900">09</span></span>
          </div>
          <div class="flex items-center justify-center py-3">
            <span>Dim <span class="items-center justify-center font-semibold text-gray-900">10</span></span>
          </div>
        </div>
      </div>
      <div class="flex flex-auto">
        <div class="sticky left-0 z-10 w-14 flex-none bg-white ring-1 ring-gray-100"></div>
        <div class="grid flex-auto grid-cols-1 grid-rows-1">
          <!-- Horizontal lines -->
          <div class="col-start-1 col-end-2 row-start-1 grid divide-y divide-gray-100" style="grid-template-rows: repeat(32, minmax(3.5rem, 1fr))">
            <div class="row-end-1 h-7"></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">6h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">7h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">8h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">9h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">10h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">11h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">12h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">13h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">14h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">15h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">16h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">17h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">18h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">19h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">20h</div>
            </div>
            <div></div>
            <div>
              <div class="sticky left-0 z-20 -ml-14 -mt-2.5 w-14 pr-2 text-right text-xs leading-5 text-gray-400">21h</div>
            </div>
            <div></div>
          </div>

          <!-- Vertical lines -->
          <div class="col-start-1 col-end-2 row-start-1 hidden grid-cols-7 grid-rows-1 divide-x divide-gray-100 sm:grid sm:grid-cols-7">
            <div class="col-start-1 row-span-full"></div>
            <div class="col-start-2 row-span-full"></div>
            <div class="col-start-3 row-span-full"></div>
            <div class="col-start-4 row-span-full"></div>
            <div class="col-start-5 row-span-full"></div>
            <div class="col-start-6 row-span-full"></div>
            <div class="col-start-7 row-span-full"></div>
            <div class="col-start-8 row-span-full w-8"></div>
          </div>

          <!-- Events -->
          <ol class="col-start-1 col-end-2 row-start-1 grid grid-cols-1 sm:grid-cols-7 sm:pr-8" style="grid-template-rows: 1.75rem repeat(288, minmax(0, 1fr)) auto">
            <!-- Monday -->
            <li class="relative mt-px flex sm:col-start-1" style="grid-row: 2 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">6h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-1" style="grid-row: 20 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">7h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-1" style="grid-row: 74 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">10h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-1" style="grid-row: 110 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">12h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-1" style="grid-row: 182 / span 27">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-pink-50 p-2 text-xs leading-5 hover:bg-pink-100">
                <p class="order-1 font-semibold text-pink-700">WOD Team</p>
                <p class="text-pink-500 group-hover:text-pink-700"><time datetime="2022-01-12T07:30">16h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-1" style="grid-row: 218 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">18h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-1" style="grid-row: 236 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">19h</time></p>
              </a>
            </li>
            
            <!-- Tuesday -->
            <li class="relative mt-px flex sm:col-start-2" style="grid-row: 20 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">7h</time></p>
              </a>
            </li>
            <li class="relative mt-px hidden sm:col-start-2 sm:flex" style="grid-row: 47 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-gray-100 p-2 text-xs leading-5 hover:bg-gray-200">
                <p class="order-1 font-semibold text-gray-700">Renfo gym</p>
                <p class="text-gray-500 group-hover:text-gray-700"><time datetime="2022-01-15T10:00">8h30</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-2" style="grid-row: 74 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">10h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-2" style="grid-row: 110 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">12h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-2" style="grid-row: 182 / span 27">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-pink-50 p-2 text-xs leading-5 hover:bg-pink-100">
                <p class="order-1 font-semibold text-pink-700">WOD Team</p>
                <p class="text-pink-500 group-hover:text-pink-700"><time datetime="2022-01-12T07:30">16h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-2" style="grid-row: 218 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">18h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-2" style="grid-row: 236 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">19h</time></p>
              </a>
            </li>

            <!-- Wednesday -->
            <li class="relative mt-px flex sm:col-start-3" style="grid-row: 2 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">6h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-3" style="grid-row: 20 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">7h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-3" style="grid-row: 74 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">10h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-3" style="grid-row: 110 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">12h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-3" style="grid-row: 182 / span 27">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-pink-50 p-2 text-xs leading-5 hover:bg-pink-100">
                <p class="order-1 font-semibold text-pink-700">WOD Team</p>
                <p class="text-pink-500 group-hover:text-pink-700"><time datetime="2022-01-12T07:30">16h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-3" style="grid-row: 218 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">18h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-3" style="grid-row: 236 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">19h</time></p>
              </a>
            </li>

            <!-- Thursday -->
            <li class="relative mt-px flex sm:col-start-4" style="grid-row: 20 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">7h</time></p>
              </a>
            </li>
            <li class="relative mt-px hidden sm:col-start-4 sm:flex" style="grid-row: 47 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-gray-100 p-2 text-xs leading-5 hover:bg-gray-200">
                <p class="order-1 font-semibold text-gray-700">Renfo gym</p>
                <p class="text-gray-500 group-hover:text-gray-700"><time datetime="2022-01-15T10:00">8h30</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-4" style="grid-row: 74 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">10h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-4" style="grid-row: 110 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">12h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-4" style="grid-row: 182 / span 27">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-pink-50 p-2 text-xs leading-5 hover:bg-pink-100">
                <p class="order-1 font-semibold text-pink-700">WOD Team</p>
                <p class="text-pink-500 group-hover:text-pink-700"><time datetime="2022-01-12T07:30">16h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-4" style="grid-row: 218 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">18h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-4" style="grid-row: 236 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">19h</time></p>
              </a>
            </li>

            <!-- Friday -->
            <li class="relative mt-px flex sm:col-start-5" style="grid-row: 2 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">6h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-5" style="grid-row: 20 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">7h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-5" style="grid-row: 74 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">10h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-5" style="grid-row: 110 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">12h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-5" style="grid-row: 182 / span 27">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-pink-50 p-2 text-xs leading-5 hover:bg-pink-100">
                <p class="order-1 font-semibold text-pink-700">WOD Team</p>
                <p class="text-pink-500 group-hover:text-pink-700"><time datetime="2022-01-12T07:30">16h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-5" style="grid-row: 218 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">18h</time></p>
              </a>
            </li>
            <li class="relative mt-px flex sm:col-start-5" style="grid-row: 236 / span 18">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-blue-50 p-2 text-xs leading-5 hover:bg-blue-100">
                <p class="order-1 font-semibold text-blue-700">WOD</p>
                <p class="text-blue-500 group-hover:text-blue-700"><time datetime="2022-01-12T06:00">19h</time></p>
              </a>
            </li>

            <!-- Saturday -->
            <li class="relative mt-px flex sm:col-start-6" style="grid-row: 20 / span 27">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-pink-50 p-2 text-xs leading-5 hover:bg-pink-100">
                <p class="order-1 font-semibold text-pink-700">WOD Team</p>
                <p class="text-pink-500 group-hover:text-pink-700"><time datetime="2022-01-12T07:30">7h</time></p>
              </a>
            </li>

            <li class="relative mt-px flex sm:col-start-6" style="grid-row: 56 / span 27">
              <a href="#" class="group absolute inset-1 flex flex-col overflow-y-auto rounded-lg bg-pink-50 p-2 text-xs leading-5 hover:bg-pink-100">
                <p class="order-1 font-semibold text-pink-700">WOD Team</p>
                <p class="text-pink-500 group-hover:text-pink-700"><time datetime="2022-01-12T07:30">9h</time></p>
              </a>
            </li>
          </ol>
        </div>
      </div>
    </div>
  </div>
</div>

</template>

<script setup>
definePageMeta({
    layout: 'dashboard'
})
</script>

<style scoped>

</style>