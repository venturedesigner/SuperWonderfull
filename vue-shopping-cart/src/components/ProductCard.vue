<template>
  <div class="productCard">
    <div class="productImage">
      <img :src="product.imageUrl" alt="">
    </div>
    <div>
      <div class="productInfo">
        <h2>{{product.name + ' ' + product.price + ' €'}}</h2>
      </div>
      <div>
        <button class="btn-green" @click="addToCart">Add to cart</button>
      </div>

    </div>
  </div>
</template>

<script>


export default {
  name: "ProductCard",
  props: {
    product: {
      type: Object
    }
  },
  methods: {
    addToCart() {
      this.$emit("addToCart", this.product)
    }
  }
}

</script>

<style scoped>
.productCard {
  width: 240px;
  height: 90px;
  display: flex;
  flex-direction:row;
  margin: 30px;
}
.productInfo{
  margin: 15px;
}
img {
  width: 100px;
  height: 100px;
  border-radius: 10px;
}
h2 {
  font-size:18px;
}
</style>