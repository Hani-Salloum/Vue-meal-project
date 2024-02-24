<template>
  <div class="flex flex-col p-8">
    <div class="p-8 pb-0 text-orange-500">
      <h1 class="text-4xl font-bold mb-4  ">Meals By Letter</h1>
    </div>

    <div class="flex justify-center gap-2 mt-2">
      <router-link :to="{name: 'byLetter', params: {letter}}" v-for="letter in letters" :key="letter" class="w-2 h-2 flex items-center justify-center hover:text-orange-500 hover:scale-150 transition-all">{{ letter }}</router-link>
    </div>

    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import { computed, onMounted, watch } from 'vue'
import store from '../store';
import { useRoute } from 'vue-router'
import Meals from '../components/Meals.vue';

const route = useRoute()
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("")
const meals = computed(() => store.state.mealsByLetter)

watch(route, () => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})

onMounted(() => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})

</script>