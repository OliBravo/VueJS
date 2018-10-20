<template>
  <div id="app">
    <add-product @add-product="onAddProduct"></add-product>

    <product-list :products="products"></product-list>

  </div>
</template>

<script>
  import ProductList from "../components/ProductList"
  import AddProduct from "../components/AddProduct"

  export default {
    name: 'app',
    components: {
        ProductList,
        AddProduct
        },
    data() {
      return {
        products: [{
          id: 0,
          name: 'item1'
        },
        {
          id: 1,
          name: 'item2'
        }]
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