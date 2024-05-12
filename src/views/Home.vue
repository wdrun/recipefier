 <template>
  <div class="p-8 pb-0 font">
    <h1 class="text-2xl drop-shadow-lg font-bold mb-4">Random Recipes</h1>
  </div>
  <Meals :meals="meals" />
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import Meals from "../components/Meals.vue";
import axiosClient from "../axiosClient.js";

const meals = ref([]);

onMounted(async () => {
  for (let i = 0; i < 10; i++) {
    axiosClient.get(`random.php`).then(({ data }) => meals.value.push(data.meals[0]));
  }
});
</script>

<style>
.font {
  color: #282828;
}
</style>
