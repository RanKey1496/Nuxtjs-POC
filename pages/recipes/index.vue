<template>
  <main class="container mt-5">
    <div class="row">
      <div class="col-12 text-right mb-4">
        <div class="d-flex justify-content-between">
          <h3>La Recipes</h3>
          <nuxt-link to="/recipes/add" class="btn btn-info">Add Recipe</nuxt-link>
        </div>
      </div>
      <template v-for="property in properties">
        <div :key="property.id" class="col-lg-3 col-md-4 col-sm-6 mb-4">
          <recipe-card :onDelete="deleteRecipe" :property="property"></recipe-card>
        </div>
      </template>
    </div>
  </main>
</template>
<script>
import RecipeCard from "~/components/RecipeCard.vue";

export default {
  head() {
    return {
      title: "Recipes list"
    };
  },
  components: {
    RecipeCard
  },
  async asyncData({ $axios, params}) {
    try {
        let response = await $axios.$get(`promotion/filter?priceStart=0&page=1&status=PROMOCION`);
        return { properties: response.data.promotions };
    } catch (e) {
        return { properties: [] };
    }
  },
  data() {
    return {
      properties: []
    };
  },
  methods: {
    deleteRecipe(recipe_id) {
      console.log(deleted `${recipe.id}`) 
    }
  }
};
</script>
<style scoped>
</style>