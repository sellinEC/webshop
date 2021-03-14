<template>
<!-- FOrm som tar in data att skicka till mongo och skpa produkter -->
<div class="container">

<form @submit.prevent="addProduct"  class="text-center border border-light p-5" action="#!">

    <p class="h4 mb-4">Add product</p>

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
    <button class="btn btn-info my-4 btn-block" type="submit">Add product</button>
    <hr>

</form>

<p>{{product}}</p>
</div>
</template>

<script>
import axios from 'axios'

// const API_URL = 'http://localhost:9999/api/products/new'
export default {
  name: 'Adminform',
  data() {
    return {
      product: {
        name: '',
        short: '',
        price: '',
        desc: '',
        image: ''
      },
    }
  },
  methods: {
    // Stulen axios-post-metod
    async addProduct() {
    let payload = { 
      name: this.product.name, 
      short: this.product.short,
      price: this.product.price,
      desc: this.product.desc,
      image: this.product.image,
    };

    let res = await axios.post('http://localhost:9999/api/products/new', payload);

    let data = res.data;
    console.log(data);
    }
  }
}
</script>

<style>

</style>