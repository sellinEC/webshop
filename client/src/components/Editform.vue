<template>
<div class="container">
  <!-- Default form register -->
<form @submit.prevent="postEditProduct"  class="text-center border border-light p-5" action="#!">

    <p class="h4 mb-4">Edit Product</p>

    <div class="form-row mb-4">
        <div class="col">
            <!-- Product name -->
            <input v-model="product.name" type="text" id="name" class="form-control" placeholder="Product name">
        </div>
        <div class="col">
            <!-- Last name -->
            <input v-model="product.short" type="text" id="short" class="form-control" placeholder="Short description">
        </div>
    </div>

    <!-- price -->
    <input v-model="product.price" type="text" id="price" class="form-control mb-4" placeholder="Price">

    <!-- description -->
    <textarea v-model="product.desc" name="description" id="" cols="20" rows="5" class="form-control mb-4" placeholder="Product description"></textarea>

    <!-- image url -->
    <input v-model="product.image" type="url" id="image" class="form-control" placeholder="image url" aria-describedby="defaultRegisterFormPhoneHelpBlock">
 

    <!-- Sign up button -->
    <button class="btn btn-info my-4 btn-block" type="submit">Edit product</button>
    <hr>

</form>
<!-- Outputs -->
<!-- edit och delete emittas från EditItem- deleten sker från EditItem men emitten "refreshar" från databasen så det syns att man deletat -->
<EditOutput @edit-product="editProduct" @delete-product="getProducts" :products="products" />
<button @click="swetter">HEJ</button>
</div>
</template>

<script>
import axios from 'axios'
import EditOutput from './EditOutput'
// const API_URL = 'http://localhost:9999/api/products/new'
export default {
  name: 'Editform',
  components: {
    EditOutput
  },
  data() {
    return {
      product: {
        name: '',
        short: '',
        price: '',
        desc: '',
        image: ''
      },
      products: []
    }
  },
  methods: {
    async postEditProduct() {
    let payload = { 
      name: this.product.name, 
      short: this.product.short,
      price: this.product.price,
      desc: this.product.desc,
      image: this.product.image,
    };

    let res = await axios.patch('http://localhost:9999/api/products/' + this.product._id, payload);

    let data = res.data;
    console.log(data);
    this.getProducts()
    },
    async getProducts() {
    const res = await axios.get('http://localhost:9999/api/products')
    this.products = res.data
    console.log(res.data,'hej');
    },
    async editProduct(id) {
      const res = await axios.get('http://localhost:9999/api/products/' +id)
      this.product = res.data
    },
    swetter() {
      console.log(this.product._id);
    }
  },
  created() {
    this.getProducts()
  }
}
</script>

<style>

</style>