<template>
  <div class="home">
    <div v-for="product in products" v-bind:key="product.id">
      Name:
      <h1>{{ product.name }}</h1>
      Description:
      <h1>{{ product.description }}</h1>
      Price:
      <h1>${{ product.price }}</h1>
      <img v-bind:src="product.image_url" :alt="product.name" contain height="300px" width="300px" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      products: [],
    };
  },
  created: function () {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      axios.get("/products").then((response) => {
        this.products = response.data;
        console.log(this.product_id);
      });
    },
  },
};
</script>
