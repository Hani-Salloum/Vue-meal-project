<template>
  <div class="bg-white shadow rounded-xl">
        <router-link :to="{name: 'mealDetails', params: {id: meal.idMeal}}">
          <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t-xl w-full h-48 object-cover">
        </router-link>
        <div class="p-5">
          <h3 class="font-bold">{{ meal.strMeal }}</h3>
          <p class="my-4">
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nisi, dolorem.
          </p>
          <div>
            <YoutubeButton :href="meal.strYoutube">Youtube</YoutubeButton>
          </div>
        </div>
      </div>
</template>

<script setup>
import YoutubeButton from '../components/YoutubeButton.vue';

const {meal} = defineProps({
  meal: {
    required: true, 
    type: Object,
  },
})

</script>