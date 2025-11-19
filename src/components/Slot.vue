<script setup>
import Parent from "./Parent.vue";
import Child from "./Child.vue";
const name = "slot name";
</script>
<template>
  <div
    style="
      margin-top: 50px;
      width: 200px;
      height: 200px;
      background-color: black;
    "
  >
    <h2>slot</h2>
    <Parent><Child /></Parent>
  </div>
</template>
