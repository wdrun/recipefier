<template>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-10 px-8">
    <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
  </div>
  <div v-if="!meals.length" class="flex justify-center font p-8">No recipes</div>
</template>

<script setup>
import MealItem from "./MealItem.vue";

const { meals } = defineProps({
  meals: {
    required: true,
    type: Array,
  },
});
</script>

<style>
.font {
  color: #282828;
}
</style>
