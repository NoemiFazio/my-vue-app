<script setup>
import { ref } from "vue";
import ProductDisplay from "@/components/ProductDisplay.vue";

const cart = ref([]);
const premium = ref(true);
const updateCart = (id) => {
  cart.value.push(id);
};
</script>

<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart.length }})</div>
  <!-- Qui sotto, la mancanza di @add-to-cart="updateCart", a differenza di react, non produce errori
  perchè le sottoscrizioni sono opzionali in vue. Invece in react ci sarebbe stato bisogno di un condizionale, ovvero
  const addToCart = () => {
  if (props.addToCart !== undefined){props.addToCart(variants[selectedVariant].id}
};
   -->
  <ProductDisplay :premium="premium" @add-to-cart="updateCart"></ProductDisplay>
</template>
