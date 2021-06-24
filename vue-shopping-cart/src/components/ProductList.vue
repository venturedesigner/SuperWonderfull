<template>
  <div class="container">
    <ProductCard 
      v-for="(product, idx) in products" :key="idx"
      :product= product
      @addToCart="addToCart"
    />
  </div>
</template>

<script>

import ProductCard from './ProductCard.vue'

export default {
  name: "ProductList",
  props: {
    products: {
      type: Array
    }
  },
  components: {
    ProductCard
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
  width:80%;
}
</style>