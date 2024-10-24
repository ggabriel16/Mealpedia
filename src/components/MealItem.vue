<template>
    <div class="bg-white shadow-xl rounded-xl hover:scale-105 transition-all flex flex-col">
        <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
            <img 
                :src="meal.strMealThumb" 
                :alt="meal.strMeal" 
                class="rounded-t-xl w-full h-56 object-cover"
            />
        </router-link>
        <div class="p-4 flex-grow">
            <h3 class="bg-orange-500 font-medium rounded-xl text-center font-serif text-xl italic tracking-wider">
                {{ meal.strMeal }}
            </h3>
            <p class="mb-4 mt-4 mr-2 ml-2">
                {{ $filters.truncateWords(meal.strInstructions, 20) }}
            </p>
        </div>
        <div class="flex items-center justify-between p-4">
            <YoutubeButton :href="meal.strYoutube" />
            <SourceButton :href="meal.strSource" />
        </div>
    </div>
</template>

<script setup>
import YoutubeButton from './YoutubeButton.vue'
import SourceButton from './SourceButton.vue'

const { meal } = defineProps({
    meal: {
        required: true,
        type: Object
    }
})
</script>
