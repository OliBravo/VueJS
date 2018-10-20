<template>
  <div id="app">
    <add-product @add-product="onAddProduct"></add-product>

    <product-list :products="products"></product-list>

  </div>
</template>

<script>
  import ProductList from "./components/ProductList"
  import AddProduct from "./components/AddProduct"

  import axios from 'axios'

  export default {
    name: 'app',
    components: {
        ProductList,
        AddProduct
        },

    async created(){
      this.products = await axios.get('https://www.booknomads.com/api/v0/isbn/9789000035526').then(res => res.data && res.data.Authors);
    },
    
    data() {
      return {
        products: []
      }
    },

    methods: {
      onAddProduct(product){
        this.products.push(product);
      }
    }
  }

</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .error-provider {
    color: red;
    font-size: 0.8em;
  }
</style>