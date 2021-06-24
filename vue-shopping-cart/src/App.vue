<template>
  <div id="app">
    <ProductList 
      :products= "Products" 
      @addToCart="addToCart"
    />
    <Cart
      :userproducts="UserProducts"
    />
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
      UserProducts: [
        {
        "id": 1,
        "name": "Banana",
        "price": 1,
        "imageUrl": "https://prodimage.images-bn.com/pimages/9781727333718_p0_v1_s550x406.jpg", 
        "quantity": 3
    }
    // {
    //     "id": 2,
    //     "name": "Apple",
    //     "price": 2,
    //     "imageUrl": "http://images.hellokids.com/_uploads/_tiny_galerie/20120416/2gr_how-to-draw-an-apple-for-kids-tutorial-drawing.jpg" , 
    //     "quantity": 4
    // }
      ]
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

</style>
