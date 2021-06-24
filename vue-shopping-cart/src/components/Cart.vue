<template>
  <div>
    <ul>
      <li>
        Product  ||   Quantity   ||   Price
      </li>
      <li v-for="(product, idx) in userproducts" :key="idx">
        {{product.name}}  ||   {{product.quantity}}  ||   {{product.price*product.quantity}}
      </li>
    </ul>
    <p>
        Total Price: {{getTotal}}
    </p>
    
    <button @click="clearCart">Clear cart</button>

  </div>
</template>

<script>


export default {
  name: "Cart",
  props: {
    userproducts: {
      type: Array
    }
  },
  computed: {
    getTotal: function () {
      let total = 0
      const sum = this.userproducts.forEach((elem) => {
        total += elem.price*elem.quantity
      })
      return total
    }
  },
  methods: {
    clearCart() {
      this.$emit("clearCart")
    }
  }
}

</script>

<style scoped>

</style>