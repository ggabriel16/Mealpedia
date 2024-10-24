<template>
    <div>
        <h1 class="text-4xl font-bold mt-4 mb-6 text-center text-orange-500 drop-shadow-[1px_0.5px_rgba(0,0,0,1)]">Meals by Letter</h1>
    </div>
    <div class="flex flex-wrap justify-center gap-3 px-8 mb-6">
        <router-link 
            v-for="letter in letters" 
            :key="letter"
            :to="{ name: 'byLetter', params: { letter } }"
            class="w-2 h-2 flex items-center justify-center hover:text-orange-500 hover:scale-150 transition-all"
        >
            {{ letter }}
        </router-link>
    </div>
    <Meals :meals="meals" />
</template>

<script setup>
import { computed, onMounted, watch } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import Meals from '../components/Meals.vue';

const route = useRoute();
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const meals = computed(() => store.state.mealsByLetter);


watch(() => route.params.letter, (newLetter) => {
    if (newLetter) {
        store.dispatch('searchMealsByLetter', newLetter);
    }
});


onMounted(() => {
    const initialLetter = route.params.letter;
    if (initialLetter) {
        store.dispatch('searchMealsByLetter', initialLetter);
    }
});
</script>
