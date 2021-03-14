<template>
<!-- Card -->
<div class="card testimonial-card">

  <!-- Background color -->
  <div class="card-up indigo lighten-1"></div>

  <!-- Avatar -->
  <div class="avatar mx-auto white">
    <img :src="product.image" class="rounded-circle"
      alt="product picture">
  </div>

  <!-- Content -->
  <div class="card-body">
    <!-- Name -->
    <h4 class="card-title">{{product.name}}</h4>
    <hr>
    <!-- Quotation -->
    <p><i class="fas fa-quote-left"></i> {{product.short}} @{{product.price}}:- price.
    </p>
    <br>
    <p>{{product.desc}}</p>
    <router-link to="#" class="btn btn-primary m-2"><i class="fas fa-shopping-basket"></i>Add to cart {{product.price}}:-</router-link>
  </div>

</div>
<!-- Card -->
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      product: {}
    }
  },
  methods: {
    async getProduct() {
      const res = await axios.get('http://localhost:9999/api/products/' + this.$route.params.id)
      this.product = res.data
    }
  },
  created() {
    this.getProduct()
  }
}
</script>

<style>

</style>