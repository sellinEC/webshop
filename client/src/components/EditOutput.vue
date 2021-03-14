<template>
<!-- Visar items att manipulera och för vidare emitten -->
  <div class="container d-flex">
    <div v-for="product in products" :key="product._id">
      <EditItem @edit-product="$emit('edit-product', product._id)" @delete-product="$emit('delete-product')" :product="product" />
    </div>
  
  </div>
</template>

<script>
import EditItem from './EditItem'
export default {
  name: 'EditOutput',
  components: {
    EditItem
  },
  props: {
    products: Array
  },
  methods: {
    // editItem(){
    //   console.log(product._id);
    // }
  }
  // data() {
  //   return {
  //     product: {
  //       _id: ''
  //     }
  //   }
  // },

}
</script>

<style>

</style>