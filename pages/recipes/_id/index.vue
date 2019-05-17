<template>
  <main class="container my-5">
    <div class="row">
      <div class="col-12 text-center my-3">
        <h2 class="mb-3 display-4 text-uppercase">{{ property.id }}</h2>
      </div>
      <div class="col-md-6 mb-4">
        <img
          class="img-fluid"
          style="width: 400px; border-radius: 10px; box-shadow: 0 1rem 1rem rgba(0,0,0,.7);"
          :src="`${property.property.images.length > 0 ? `https://assets.arrendamientosnutibara.com/spaces/images/${property.property.id}/350${property.property.images[0].resource}` : `https://assets.arrendamientosnutibara.com/spaces/images/7661/350a861db299cd5979816d1cad6f6baaeb4.jpg`}`"
          alt
        >
      </div>
      <div class="col-md-6">
        <div class="recipe-details">
          <h4>Valor</h4>
          <p>{{ property.rentValue }}</p>
          <h4>Estado</h4>
          <p>{{ property.status }}</p>
          <h4>Tipo</h4>
          <p>{{ property.property.type }}</p>
          <h4>Barrio</h4>
          <p>{{ property.property.neighborhood }}</p>
          <h4>Ciudad</h4>
          <textarea class="form-control" rows="10" v-html="property.property.city" disabled />
        </div>
      </div>
    </div>
  </main>
</template>
<script>
export default {
  head() {
    return {
      title: "View Recipe"
    };
  },
  async asyncData({ $axios, params }) {
    try {
      let result = await $axios.$get(`/promotion/${params.id}`);
      return { property: result.data };
    } catch (e) {
      return { property: {} };
    }
  },
  data() {
    return {
      property: {
        id: "",
        rentValue: "",
        status: "",
        property: {
            type: "",
            neighborhood: "",
            city: "",
            images: [
            ]
        }
      }
    };
  }
};
</script>
<style scoped>
</style>