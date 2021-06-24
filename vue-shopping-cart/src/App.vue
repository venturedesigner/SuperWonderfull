<template>
  <div id="app">
    <ProductList 
      :products= "Products" 
    />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue'
import ProductsData from '@/assets/products.json' 

export default {
  name: 'App',
  data() {
    return {
      Products: ProductsData
    }
  },
  components: {
    ProductList
  }
}
</script>

<style>

</style>
