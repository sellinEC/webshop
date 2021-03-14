<template>
<div>
  <h1>Products</h1>
  <ProductsOutput :products="products"/>
  </div>
</template>

<script>
import axios from 'axios'
import ProductsOutput from '../components/ProductsOutput'
export default {
  name: 'Products',
  components: {
    ProductsOutput
  },
  data() {
    return {
      products: []
    }
  },
  methods: {
    async getProducts() {
      const res = await axios.get('http://localhost:9999/api/products')
      this.products = res.data
    }
  },
  mounted() {
    this.getProducts()
  }
}
</script>

<style>

</style>