<template>
<!-- Sida med switch mellan add product och edit product, enkel toggle -->
<div class="container">
  <h1>Admin</h1>
  <button @click="toggleAdd" class="btn btn-primary m-2">{{action}}</button>
  <keep-alive>
  <Adminform v-if="showAdd" />
  </keep-alive>
  <keep-alive>
  <Editform v-if="!showAdd" />
  </keep-alive>
</div>
</template>

<script>
import Adminform from '../components/Adminform'
import Editform from '../components/Editform'
export default {
  components: {
    Adminform,
    Editform
  },
  data() {
    return {
      showAdd : true,
      action: 'Edit',
      products: []
    }
  },
  methods: {
    toggleAdd() {
      this.showAdd = !this.showAdd
      if(this.showAdd){
        this.action = 'Edit'
      }else{
        this.action = 'Add'
      }
    },
  },

}
</script>

<style>

</style>