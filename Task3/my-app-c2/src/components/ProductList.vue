<template>
  <div id="app">
    <!-- 7. We can use Angular-like double brackets to create an expression -->
    <li v-for="i in products" :key="i.id">{{i.name}}</li>
  </div>
</template>

<script>
  export default {
    name: "ProductList",
    props: {
      products: {
        type: Array
      }
    },

    methods: {
      onSubmit() {
        this.$validator.validateAll().then(result => {
          if (!result) {
            return;
          }
          this.products.push({ name: this.name });
          this.name = '';
          this.$validator.reset();
        })

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