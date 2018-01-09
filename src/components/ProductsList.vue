<template>
  <div>
    <h1>Lista Produktów :</h1>
    <ul>
      <li v-for="product in products" >{{ product.name }} - {{ product.price }}zl</li>
    </ul>
    <form>
      <input type="text" placeholder="Nazwa produktu" v-model="newProduct.name">
      <input v-on:keyup.enter="addProduct" type="number" placeholder="Cena produktu" v-model="newProduct.price">
      <button v-on:click="addProduct" type="button" name="button">Dodaj produkt</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data () {
    return {
      products: [],
      newProduct: {
        name: '',
        price: ''
      }
    }
  },
  created () {
    this.getProducts();
  },
  methods: {
    getProducts () {
      axios.get('http://localhost:3000/products')
      .then( (response) => {
        if (response.status === 200) {
          this.products = response.data;
        }
      })
      .catch( (error) => {
        console.log(error);
      });
    },
    addProduct() {
      axios.post('http://localhost:3000/products', {
        name: this.newProduct.name,
        price: this.newProduct.price
      })
      .then( (response) => {
        if (response.status === 201) {
          this.getProducts();
          this.newProduct.name = '';
          this.newProduct.price = '';
        }
        console.log(response);
      })
      .catch( (error) => {
        console.log(error);
      });
    }
  }
}

</script>

<style lang="scss">

</style>
