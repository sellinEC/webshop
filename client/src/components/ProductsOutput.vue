<template>
  <div class="container d-flex">
    <div class="row d-flex">

      <div v-for="(product, index) in products" :key="index" class="col-3">
          <div class="card">
          <div class="bg-image hover-overlay ripple" data-mdb-ripple-color="light">
          <img
          :src="product.image"
          class="img-fluid"
        />
        <a href="#!">
          <div class="mask" style="background-color: rgba(251, 251, 251, 0.15)"></div>
        </a>
        </div>
        <div class="card-body">
        <h5 class="card-title">{{product.name}}</h5>
        <p class="card-text">
          {{product.short}}
        </p>
        <a href="#!" class="btn btn-primary m-2">Buy</a>
        <router-link :to="'/products/details/' + product._id" class="btn btn-primary m-2">Details</router-link>
        </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
// import Product from '../components/Product'
export default {
  name: 'Productsoutput',
  components: {
    // Product
  },
  props:{
    products: Array,
  }
}
</script>

<style>

</style>