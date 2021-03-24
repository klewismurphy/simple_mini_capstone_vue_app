<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-bind:key="product.id" v-for="product in products">
    {{ product.name }}
    </div>
    <br><hr><br>
    <p> Name: <input type="text" v-model="name"></p>
    <p> Description: <input type="text" v-model="description"></p>
    <p> Price: <input type="number" v-model="price"></p>
    <p> Image Url: <input type="text" v-model="image_url"></p>
    <button v-on:click="createProducts">Create a Product</button>
  </div>
</template>

<style></style>



<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "HEY",
      products: [],
      name: "",
      description: "",
      price: "",
      image_url: "",
    };
  },
  created: function () {
    this.indexProducts("success");
  },
  methods: {
    indexProducts: function () {
      console.log("getting products...");
      axios.get("http://localhost:3000/api/products").then((response) => {
        console.log(response.data);
        this.products = response.data;
      });
    },
    createProducts: function () {
      console.log("creating a product...");
      axios
        .post("http://localhost:3000/api/products", {
          name: this.name,
          description: this.description,
          price: this.price,
          image_url: this.image_url,
        })
        .then((response) => {
          console.log(response.data);
          this.products.push(response.data);
        });
    },
  },
};
</script>
