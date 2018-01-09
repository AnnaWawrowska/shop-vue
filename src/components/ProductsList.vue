<template>
  <div>
    <h1>Lista Produktów :</h1>
    <ul>
      <li v-for="product in products" >{{ product.name }} - {{ product.price }}zl</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data () {
    return {
      products: [],
    }
  },
  created () {
    axios.get('http://localhost:3000/products')
    .then( (response) => {
      if (response.status === 200) {
        this.products = response.data;
      }
    })
    .catch( (error) => {
      console.log(error);
    });
  }
}

</script>

<style lang="scss">

</style>
