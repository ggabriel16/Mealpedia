<template>
    <div>
        <h1 class="text-4xl font-bold mt-4 mb-6 text-center text-orange-500 drop-shadow-[1px_0.5px_rgba(0,0,0,1)]">Ingredients</h1>
    </div>
    <div class="px-8">
      <input
        type="text"
        v-model="keyword"
        class="rounded border-2 bg-white border-gray-200 focus:ring-orange-500 focus:border-orange-500 mb-3 p-2 w-full"
        placeholder="Search for Ingredients"
      />
      <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
        <a href="#"
          @click.prevent="openIngredient(ingredient)"
          v-for="ingredient of computedIngredients"
          :key="ingredient.idIngredient"
          class="block bg-white rounded-xl p-1 mb-2 shadow hover:scale-105 transition-all"
        >
          <h3 class="text-2xl font-semibold mt-2 mb-2 text-center">{{ ingredient.strIngredient }}</h3>
        </a>
      </div>
    </div>
  </template>
  
  <script setup>
  import { computed } from "@vue/reactivity";
  import { onMounted, ref } from "vue";
  import { useRouter } from "vue-router";
  import axiosClient from "../axiosClient";
  import store from "../store";
  
  const router = useRouter();
  const keyword = ref("");
  const ingredients = ref([]);
  const computedIngredients = computed(() => {
    if (!computedIngredients) return ingredients;
    return ingredients.value.filter((i) =>
      i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
    );
  });
  
  function openIngredient(ingredient) {
    store.commit('setIngredient', ingredient)
    router.push({
      name: "byIngredient",
      params: { ingredient: ingredient.strIngredient },
    });
  }
  
  onMounted(() => {
    axiosClient.get("list.php?i=list").then(({ data }) => {
      ingredients.value = data.meals;
    });
  });
  </script>