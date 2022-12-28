<template>
  <Navbar/>
  <router-view/>
</template>

<script>
import Navbar from './components/Navbar.vue'
export default{
  components: {
    Navbar,
  },
}
</script>

<style>
@import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
@import '../node_modules/bootstrap-icons/font/bootstrap-icons.css';
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap');

body{
  font-family: 'Roboto', sans-serif;
  background-color : #e0c45c;
}
</style>
