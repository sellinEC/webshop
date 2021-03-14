<template>
<div>
  <button class="btn btn-primary m-2"><i @click="editProduct(product._id)" class="fas fa-edit"></i> {{product.name}} <i @click="sendDeleteRequest" class="fas fa-trash-alt"></i></button>
</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'EditItem',
  props: {
    product: Object
  },
  methods: {
    deleteProduct(){
      console.log(this.product._id, 'delete');
    },
    editProduct(id){
      this.$emit('edit-product', id);
      // console.log(id);
    },
    async sendDeleteRequest() {
    try {
        const resp = await axios.delete('http://localhost:9999/api/products/'+ this.product._id)
        console.log(resp.data);
    } catch (err) {
        // Handle Error Here
        console.error(err);
    }
    this.$emit('delete-product')
    }
  }
}
</script>

<style scoped>
i{
  font-size: 1.5rem;
  padding: 1rem;
}
.fa-trash-alt{
  color: red;
}
.fa-edit {
  color: greenyellow
}

</style>