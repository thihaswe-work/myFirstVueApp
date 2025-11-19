<script setup>
import { ref } from "vue";
import ProductDisplay from "./components/ProductDisplay.vue";
const show = ref(true);
const preminum = ref(false);
const cart = ref(0);
const addToCart = () => (cart.value += 1);
</script>

<template>
  <div v-if="show">Show is true</div>
  <div v-else>Show is false</div>
  <h1 v-show="show">Show Status of Vue</h1>
  <div>cart {{ cart }}</div>
  <button :disabled="cart === 0" @:click="cart -= 1">remove from cart</button>
  <ProductDisplay v-bind:preminum="preminum" v-on:add-to-cart="addToCart" />
</template>

<style scoped></style>
