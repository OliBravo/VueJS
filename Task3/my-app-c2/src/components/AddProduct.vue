<template>
  <div id="app">
    <form @submit.prevent="onSubmit()">
      <button>Add new item</button>
      <input name="newitem"  v-model="newProduct.Name">
      <!-- <div v-show="errors.has('newitem')" class="error-provider">
        {{ errors.first('newitem') }}
      </div> -->
    </form>
  </div>
</template>

<script>
  export default {
    name: 'AddProduct',
    data() {
      return {
        newProduct: {
          Name: ''
        }
      }
    },

    methods: {
      onSubmit() {
        //this.$validator.validateAll().then(result => {
        //  if (!result) {
        //    return;
        //  } -->
        this.$emit('add-product',{ 
            ...this.newProduct
        }
          );
          this.newProduct.Name = '';
          //this.$validator.reset();
        //})

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