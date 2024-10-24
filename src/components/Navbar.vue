<template>
    <header class="bg-white shadow-md  h-16 flex justify-between items-stretch">
         <router-link :to="{name: 'home'}" class="font-bold inline-flex items-center h-full px-5 transition-colors hover:bg-orange-500 text-orange-500 hover:text-white">
             Home
         </router-link>
         <div class="flex items-center gap-1">
            <router-link :to="{name: 'byName'}" class="mr-2 font-semibold  inline-flex items-center px-2 h-full transition-colors hover:bg-orange-500 hover:text-white">
                Search Meals
            </router-link>
            <router-link :to="{name: 'byLetter'}" class="mr-2 font-semibold  inline-flex items-center px-2 h-full transition-colors hover:bg-orange-500 hover:text-white">
                Meals by Letter
            </router-link>
            <router-link :to="{name: 'ingredients'}" class="mr-2 font-semibold inline-flex items-center px-2 h-full transition-colors hover:bg-orange-500 hover:text-white">
                Meals by Ingredients
            </router-link>
         </div>
 
     </header>
</template>