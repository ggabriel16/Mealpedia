<template>
    <div>
      <h1 class="text-4xl font-bold mt-4 mb-6 text-center text-orange-500 drop-shadow-[1px_0.5px_rgba(0,0,0,1)]">Meals with {{ ingredient.strIngredient.toLowerCase() }}</h1>
    </div>
  
    <Meals :meals="meals" />
  </template>
  
  <script setup>
  import { computed } from "@vue/reactivity";
  import { onMounted } from "vue";
  import { useRoute } from "vue-router";
  import store from "../store";
  import Meals from '../components/Meals.vue'
  
  const route = useRoute();
  const ingredient = computed(() => store.state.ingredient)
  const meals = computed(() => store.state.mealsByIngredient)
  
  onMounted(() => {
    store.dispatch('searchMealsByIngredient', route.params.ingredient)
  })
  
  </script>