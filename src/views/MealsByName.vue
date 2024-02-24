<template>
  <div>
    <div class="p-8 pb-0 text-orange-500">
      <h1 class="text-4xl font-bold mb-4">Search Meals</h1>
    </div>

    <div class="p-8 pb-0">
      <input type="text" v-model="keyword" class="rounded border-2 bg-white border-gray-200 focus:ring-orange-500 focus:border-orange-500 mb-3 w-full" placeholder="Search for Meals"
        @change="searchMeals">
    </div>

    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import store from '../store';
import { computed, ref, onMounted } from 'vue';
import {useRoute} from 'vue-router'
import MealItem from '../components/MealItem.vue';
import Meals from '../components/Meals.vue';


const route = useRoute();
const keyword = ref('')
const meals = computed(() => store.state.searchedMeals)

function searchMeals() {
  if(keyword.value) {
    store.dispatch('searchMeals', keyword.value)
  } else {
    store.commit("setSearchedMeals", [])
  }
}

onMounted(() => {
  keyword.value = route.params.name
  if(keyword.value) {
    searchMeals()
  }
})

</script>