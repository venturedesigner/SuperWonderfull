<template>
  <div>
    <input @keyup="searchLookup" v-model="SearchTerm" type="text" placeholder="Search here">
    <!-- <button @click="searchLookup" > Search </button> -->
  </div>
</template>

<script>

export default {
  name: "SearchBar",
  data() {
    return {
      SearchTerm: ''
    }
  },
  methods: {
    searchLookup() {
      this.$root.$emit("searchLookup", this.SearchTerm)
    }
  }
}

</script>

<style scoped>
 input {
    border-radius: 55px;
    height: 10px;
    border: none;
    width: 70%;
    padding: 15px;
 }
 
</style>