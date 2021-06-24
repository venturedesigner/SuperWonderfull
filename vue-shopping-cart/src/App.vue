<template>
  <div id="app">
    <div id="productListContainer">
      <ProductList 
        :products= "Products" 
        @addToCart="addToCart"
      />
    </div>
    <div id="CartContainer">
      <Cart
        :userproducts="UserProducts"
      />
    </div>
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue'
import ProductsData from '@/assets/products.json' 
import Cart from '@/components/Cart.vue'

export default {
  name: 'App',
  data() {
    return {
      Products: ProductsData,
      UserProducts: []
    }
  },
  components: {
    ProductList,
    Cart
  },
  methods: {

    addToCart(product) {
      console.log('--> Abuelo' ,product, )
      if (this.UserProducts.filter(p => p.id === product.id).length > 0) {
        const productQuantityIncreased = this.UserProducts.filter(p => p.id === product.id)[0]
        this.$set(productQuantityIncreased, productQuantityIncreased.quantity, productQuantityIncreased.quantity++)
      } else {
        product.quantity = 1
        this.UserProducts.push(product)
      }
    }
  }
}
</script>

<style>
#productListContainer {
  width:60%;
  display:inline-block;
}
#CartContainer {
  width:30%;
  display:inline-block;
  position:fixed;
}
</style>
