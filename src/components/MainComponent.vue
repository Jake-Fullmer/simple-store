<template>
  <div class="pt-3" id="main-component">
    <div class="product container-fluid">
      <div class="row">
        <div class="col-12 col-sm-8">
          <div class="product-image">
            <img class="image-size" :src="image" />
            <hr class="hr" />
            <div class="row justify-content-center">
              <div v-for="(variant, index) in variants" :key="variant.variantId">
                <img
                  class="image-size-alt"
                  :src="variant.variantImg"
                  @mouseover="updateProduct(index)"
                />
              </div>
            </div>
          </div>
        </div>
        <div class="col-12 col-sm-4">
          <div class="onSale mt-3">
            <p v-if="onSale" class="on-sale">On Sale Now!</p>
          </div>
          <div class="product-info">
            <h3>{{ title }}</h3>
            <p v-if="inventory > 10">In Stock</p>
            <p
              class="low-supply"
              v-else-if="inventory <= 10 && inventory > 0"
            >Order Soon! Only {{inventory}} Remaining</p>
            <p v-else :class="{ line: !inStock }">Out of Stock</p>
          </div>
          <ul class="list">
            <li v-for="detail in details" :key="detail">{{ detail }}</li>
          </ul>
          <button
            @click="addToCart"
            :disabled="!inStock"
            :class="{ disabledButton: !inStock }"
            class="btn btn-outline-success btn-sm"
          >Add to Cart</button>
          <button @click="decrementCart" class="btn btn-outline-danger btn-sm ml-1">X</button>
          <div class="cart">
            <p>Cart ({{ cart }})</p>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-6">
          <div v-for="size in sizes" :key="size">
            <p>{{ size }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import black from "../assets/black.jpg";
import white from "../assets/white.jpg";
import green from "../assets/green.jpg";
import blue from "../assets/blue.jpg";
export default {
  name: "App",
  data() {
    return {
      brand: "The Tee Co",
      product: "Coffee into Code Tee",
      // image: black,
      selectedVariant: 0,
      inventory: 0,
      onSale: true,
      details: ["50% Cotton", "50% Polyester"],
      variants: [
        {
          variantId: 6881,
          variantColor: "Black",
          variantImg: black,
          variantQuantity: 7
        },
        {
          variantId: 6882,
          variantColor: "Blue",
          variantImg: blue,
          variantQuantity: 11
        },
        {
          variantId: 6884,
          variantColor: "White",
          variantImg: white,
          variantQuantity: 0
        },
        {
          variantId: 6883,
          variantColor: "Green",
          variantImg: green,
          variantQuantity: 15
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
    decrementCart() {
      this.cart -= 1;
    },
    updateProduct(index) {
      this.selectedVariant = index;
    }
  },
  computed: {
    title() {
      return this.brand + " " + this.product;
    },
    image() {
      return this.variants[this.selectedVariant].variantImg;
    },
    inStock() {
      return this.variants[this.selectedVariant].variantQuantity;
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
.image-size {
  height: 55vh;
  padding: 1rem;
}
.image-size-alt {
  height: 20vh;
  padding: 1rem;
}
.product-image {
  border: 1px solid gray;
}
.on-sale {
  background-color: red;
  color: white;
  padding-top: 0.2rem;
  padding-bottom: 0.2rem;
}
.low-supply {
  color: red;
}
hr.hr {
  border: 0.2px solid gray;
}
.list {
  // display: flex;
  text-align: left;
}
.disabledButton {
  background-color: rgb(22, 0, 0) !important;
}
.line {
  text-decoration: line-through;
}
</style>

