<template>
    <div>
        <h1 class="text-4xl font-bold mt-4 mb-6 text-center text-orange-500 drop-shadow-[1px_0.5px_rgba(0,0,0,1)]">Meals by Name</h1>
    </div>
    <div class = "p-2 pb-4">
        <input 
         type = "text" 
         v-model="keyword"
         class = "rounded border-2 bg-white border-gray-200 w-full h-10 hover:border-orange-500 focus:border-orange-400"
         placeholder = " Search for meals!"
         @change = "searchMeals"
         />
    </div>

    <Meals :meals="meals" />
</template>

<script setup>
import { computed } from '@vue/reactivity'
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import Meals from '../components/Meals.vue';

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
    if (keyword.value){
        store.dispatch('searchMeals', keyword.value);
    } else {
        store.commit('setSearchedMeals', []);
    }
}

onMounted(()=> {
    keyword.value = route.params.name
    if (keyword.value) {
        searchMeals()
    }
})

</script>