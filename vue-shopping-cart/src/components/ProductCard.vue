<template>
  <div class="productCard">
    <p>{{product.name}}</p>
    <h2>{{product.price + ' €'}}</h2>
    <img :src="product.imageUrl" alt="">
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
}

</script>

<style scoped>
.productCard {
  width:300px;
  height:300px;
}
img {
  width:180px;
  height:180px;
}
</style>