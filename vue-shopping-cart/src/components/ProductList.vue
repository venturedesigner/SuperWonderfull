<template>
  <div>
    <div class="searchContainer">
      <h1>Mr SuperWonderful</h1>
      <div class="searchBox">
        <SearchBar/>  
      </div>
    </div>
    <div class="container">
      <ProductCard 
        v-for="(product, idx) in products" :key="idx"
        :product= product
        @addToCart="addToCart"
      />
    </div>
  </div>
</template>

<script>

import ProductCard from './ProductCard.vue'
import SearchBar from './SearchBar.vue'

export default {
  name: "ProductList",
  props: {
    products: {
      type: Array
    }
  },
  components: {
    ProductCard,
    SearchBar
  },
  methods: {
    addToCart(product) {
      console.log('--> padre', product)
      this.$emit("addToCart", product)
    }
  }
}

</script>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
.searchContainer{
  height:70px;
  display: flex;
  justify-content:space-between;
  background-color: #86138C;
  align-items: center;
}
.searchBox{
  width:50%;
}
h1{
  color:white;
  font-size:27px;
  margin-left: 18px;;
}
</style>