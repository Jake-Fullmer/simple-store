<template>
  <div id="app">
    <div class="product">
      <div class="product-image">
        <img :src="image" />
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inventory > 10">In Stock</p>
        <p v-else-if="inventory <= 10 && inventory > 0">Order Soon! Only {{inventory}} Remaining</p>
        <p v-else>Out of Stock</p>
      </div>
      <div class="onSale">
        <p v-if="onSale">On Sale Now!</p>
      </div>
      <ul>
        <li v-for="detail in details" :key="detail">{{ detail }}</li>
      </ul>
      <div v-for="variant in variants" :key="variant.variantId">
        <p @mouseover="updateProduct(variant.variantImg)">{{ variant.variantColor }}</p>
      </div>
      <div v-for="size in sizes" :key="size">
        <p>{{ size }}</p>
      </div>
      <button @click="addToCart" class="btn btn-outline-success btn-sm">Add to Cart</button>
      <div class="cart">
        <p>Cart ({{ cart }})</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      product: "Shirt",
      image: "./assets/stopped-coding-tee-shirt.jpg",
      inventory: 7,
      onSale: true,
      details: ["50% Cotton", "50% Polyester"],
      variants: [
        {
          variantId: 6881,
          variantColor: "Black",
          variantImg: "../assets/black.jpg"
        },
        {
          variantId: 6882,
          variantColor: "White",
          variantImg: "./assets/white.jpg"
        }
      ],
      sizes: ["XXL", "XL", "L", "M", "S"],
      cart: 0
    };
  },
  methods: {
    addToCart() {
      this.cart += 1;
    },
    updateProduct(variantImg) {
      this.image = variantImg;
    }
  }
};
</script>

<style lang="scss">
@import "bootstrap";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

