<template>
  <div class="card recipe-card">
    <img :src="`${property.property.images.length > 0 ? `https://assets.arrendamientosnutibara.com/spaces/images/${property.property.id}/350${property.property.images[0].resource}` : `https://assets.arrendamientosnutibara.com/spaces/images/7661/350a861db299cd5979816d1cad6f6baaeb4.jpg`}`" class="card-img-top" >
    <div class="card-body">
      <h5 class="card-title">{{ property.rentValue }}</h5>
      <p class="card-text">
        <strong>{{ property.status }}</strong>
      </p>
      <div class="action-buttons">
        <nuxt-link :to="`/recipes/${property.id}/`" class="btn btn-sm btn-success"> View </nuxt-link>
        <nuxt-link :to="`/recipes/${property.id}/edit/`" class="btn btn-sm btn-primary"> Edit </nuxt-link>
        <button @click="onDelete(property.id)"  class="btn btn-sm btn-danger">Delete</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
    props: ["property", "onDelete"]
};
</script>
<style>
.recipe-card {
    box-shadow: 0 1rem 1.5rem rgba(0,0,0,.6);
}
</style>