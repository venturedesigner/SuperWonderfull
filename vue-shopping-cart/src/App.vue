<template>
  <div id="app">
    <div id="productListContainer">
      <ProductList 
        :products= "filteredProducts" 
        @addToCart="addToCart"
      />
    </div>
    <div id="CartContainer">
      <Cart
        :userproducts="UserProducts"
        @clearCart="clearCart"
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
      Search: '',
      Products: ProductsData,
      UserProducts: []
    }
  },
  components: {
    ProductList,
    Cart
  },
  computed: {
    filteredProducts () {
      return this.Products.filter( p => {
        const name = p.name.toLowerCase()
        const searchTerm = this.Search.toLowerCase() 
        return name.includes(searchTerm)
      } )
    }
  },
  methods: {
    clearCart() {
      this.UserProducts = []
    },
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
  },
  mounted() {
    this.$root.$on("searchLookup", (SearchTerm) => {
      this.Search = SearchTerm
    })
  }
}
</script>

<style>
#productListContainer {
  width:70%;
  display:inline-block;
}
#CartContainer {
  width:30%;
  display:inline-block;
  position:fixed;
}
.btn-green {
  margin: 20px;
  background-color: #2fb02f;
  border: none;
  border-radius: 10px;
  padding: 4px 12px;
  color: white;
}
.btn-blue {
  margin: 20px;
  background-color: #2f58b0;
  border: none;
  border-radius: 10px;
  padding: 4px 12px;
  color: white;
}
body {
  margin: 0px;
}
</style>
