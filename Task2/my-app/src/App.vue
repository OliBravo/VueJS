<template>
  <div id="app">
    <form @submit.prevent="onSubmit()">
      <button>Add new item</button>
      <input name="newitem"  v-model="name" v-validate="'required'">
      <div v-show="errors.has('newitem')" class="error-provider">
        {{ errors.first('newitem') }}
      </div>
    </form>

    <!-- 7. We can use Angular-like double brackets to create an expression -->
    <li v-for="i in mylist">{{i.name}}</li>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data() {
      return {
        mylist: [{
          id: 0,
          name: 'item1'
        },
        {
          id: 1,
          name: 'item2'
        }],
        name: ''
      }
    },

    methods: {
      onSubmit() {
        this.$validator.validateAll().then(result => {
          if (!result) {
            return;
          }
          this.mylist.push({ name: this.name });
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