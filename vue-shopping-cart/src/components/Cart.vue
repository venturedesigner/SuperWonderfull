<template>
<div>
  <table>

    <tr>
      <th>Product</th>
      <th>Quantity</th>
      <th>Price</th>
    </tr>

    <tr v-for="(product, idx) in userproducts" :key="idx">
      <td>{{product.name}} </td>
      <td> {{product.quantity}} </td>
      <td> {{product.price*product.quantity}} </td>
    </tr>

    <tr>
      <th>Total</th>
      <th></th>
      <th>{{getTotal}}</th>
    </tr>

  </table>

  <button class="btn-blue" @click="clearCart">Clear cart</button>
</div>

  <!-- <div>
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

  </div> -->
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
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #f2deff;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #f2deff;
}
</style>