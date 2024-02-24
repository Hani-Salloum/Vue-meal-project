<template>
  <!-- <div class="p-8">
    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
      <MealItem v-for="meal in meals" :key="meal.idMeal" :meal="meal"/>
    </div> 
    <div v-if="!meals.length" class="flex justify-center text-gray-600">
      There are no meals!
    </div>
  </div> -->
  <Meals :meals="meals"/>
</template>

<script setup>
import { computed } from "@vue/reactivity";
import { onMounted, ref } from 'vue'
import store from '../store';
import { useRoute } from 'vue-router'
import Meals from '../components/Meals.vue';

const route = useRoute()
const meals = computed(() => store.state.mealsByIngredient)

onMounted(() => {
  store.dispatch('searchMealsByIngredient', route.params.ingredient)
})
</script>