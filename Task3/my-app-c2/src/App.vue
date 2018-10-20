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
      this.products = await axios.get('products.json').then(res => res.data);
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