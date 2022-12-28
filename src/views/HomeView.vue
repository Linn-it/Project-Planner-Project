<template>
  <FilterNav :current="current" @filterVal="filterVal"/>
  <div class="mt-2 mt-md-4">
    <div v-for="product in FilterProducts">
    <Product :product="product" @deleteProduct="deleteProduct" @checkProduct="checkProduct"/>
  </div>
  </div>
</template>

<script>
import Product from '../components/Product.vue';
import FilterNav from '../components/FilterNav.vue';
import { allGeneratedPositionsFor } from '@jridgewell/trace-mapping';
  export default {
    data() {
      return {
        products: [],
        current : 'all',
      }
    },
    methods: {
      deleteProduct(id) {
        this.products = this.products.filter(product => product.id !== id);
      },
      checkProduct(id){
        const updateCheck = this.products.find(product => product.id === id);
        updateCheck.isDone = !updateCheck.isDone;
      },
      filterVal(value){
        this.current = value;
      }
    },
    components: {
      Product,
      FilterNav,
    },
    computed: {
      FilterProducts() {
        if(this.current === 'complete'){
          return this.products.filter(product => product.isDone)
        }else if(this.current === 'ongoing'){
          return this.products.filter(product => !product.isDone)
        }
        return this.products;
      }
    },
    mounted () {
      fetch('http://localhost:3000/Product')
      .then(response => response.json())
      .then(datas => this.products = datas)
    },
  }
</script>

<style lang="scss" scoped>

</style>
