<template>
  <div>
    <productsList></productsList>
    <shoppingCart></shoppingCart>
  </div>
</template>

<script>
import ProductsList from './components/ProductsList';
import ShoppingCart from './components/ShoppingCart';

export default {
  components: {
    'productsList': ProductsList,
    'shoppingCart': ShoppingCart
  },
  data () {
    return {

    }
  }
}
</script>

<style lang="scss">

</style>
