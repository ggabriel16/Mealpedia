<template>
    <div>
        <h1 class="text-4xl font-extrabold mt-4 mb-6 text-center text-orange-500 drop-shadow-[1px_0.5px_rgba(0,0,0,1)]">Explore New Meals</h1>
    </div>
    <Meals :meals="meals" />
  </template>
  
  <script setup>
  import { onMounted, ref } from "vue";
  import Meals from "../components/Meals.vue";
  import axiosClient from "../axiosClient.js";
  
  const meals = ref([]);
  
  onMounted(async () => {
    for (let i = 0; i < 10; i++) {
      axiosClient
        .get(`random.php`)
        .then(({ data }) => meals.value.push(data.meals[0]));
    }
  });
  </script>