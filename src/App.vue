<script setup>
import {
  ref,
  // reactive
} from "vue";
import socksGreenImage from "./assets/images/socks_green.jpeg";
import socksBlueImage from "./assets/images/socks_blue.jpeg";
//sotto è equivalente dello useState di react
const product = ref("Socks");
const image = ref(socksGreenImage);
//commentato perchè non serve
// const inventory = ref(8);
const inStock = ref(false);
const details = ref(["50% cotton", "30% wool", "20% polyester"]);
const variants = ref([
  { id: 2234, color: "green", image: socksGreenImage },
  { id: 2235, color: "blue", image: socksBlueImage },
]);
const cart = ref(0);

const addToCart = () => (cart.value += 1);
const updateImage = (variantImage) => {
  image.value = variantImage;
};

//commentato perchè non serve
// setTimeout(() => {
//   product.value= "Ciaone"
// }, 1000)

// il codice sopra i può scrivere anche così, di solito se abbiamo un oggetto:
// const product = reactive({ name: "Hola"})
// setTimeout(() => {
//   product.name= "Ciaone"
// }, 1000)

// esempio di come scrivere un custom hook:
// const useChangeWithDelay = function(state, newVal, delay){
//   setTimeout(() => {
//   state.value= newVal
// }, delay)
// }
// useChangeWithDelay(product, "New Socks", 1000)
</script>

<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img v-bind:src="image" alt="" />
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inStock">In stock</p>
        <p v-else>Out of stock</p>
        <!-- <p v-if="inventory > 10">In stock</p>
        <p v-else-if="inventory <= 10 && inventory > 0">Almost sold out!</p>
        <p v-else>out of stock</p> -->
        <!-- <p v-show="inStock">In Stock</p> -->
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <div
          v-for="variant in variants"
          :key="variant.id"
          @mouseover="updateImage(variant.image)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        ></div>
        <button
          class="button"
          :class="{ disabledButton: !inStock }"
          v-on:click="addToCart"
          :disabled="!inStock"
        >
          Add to Cart
        </button>
      </div>
    </div>
  </div>
</template>
