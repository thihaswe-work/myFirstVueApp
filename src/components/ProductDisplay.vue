<script setup>
import { ref, computed } from "vue";
import logo from "@/assets/logo.svg";

const props = defineProps({
  preminum: {
    type: Boolean,
    required: true,
  },
});

const emit = defineEmits(["add-to-cart"]);

const image = ref(logo);

const details = ref([
  { id: 1, color: "red" },
  { id: 2, color: "blue" },
]);

const ulStyles = {
  display: "flex",
  "flex-direction": "column",
  gap: "10px",
  "margin-top": "50px",
};

const addToCart = () => {
  emit("add-to-cart");
};
const variantColor = ref(details.value[0].color);

const updateColor = (color) => {
  variantColor.value = color;
};
const shipping = computed(() => {
  if (props.preminum) return "free";
  else return "2.99";
});
</script>

<template>
  <div>
    <h5>shipping fee is {{ shipping }}</h5>
    <img v-bind:src="image" />
    <h2 v-bind:style="{ color: variantColor }">variant color</h2>
    <div>
      <button v-on:click="addToCart">add to cart</button>
    </div>
    <ul :style="ulStyles">
      <li
        class="list"
        v-for="detail in details"
        v-bind:style="{ backgroundColor: detail.color }"
        v-bind:key="detail.id"
        v-on:mouseover="
          () => {
            updateColor(detail.color);
          }
        "
      ></li>
    </ul>
  </div>
</template>

<style scoped>
.list {
  width: 50px;
  height: 50px;
  border-radius: 50%;
}
</style>
