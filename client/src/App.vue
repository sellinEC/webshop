<template>
<div>
  <Navbar />

    <!-- <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> -->

  <router-view/>
  </div>
</template>
<script>

import Navbar from './components/Navbar.vue'
export default {
  name: 'Home',
  components: {
    Navbar

  }
}
</script>
<style>

</style>
