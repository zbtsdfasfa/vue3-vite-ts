<script setup>
import Check from "./components/Check.vue";
let top = 45;

const getPosition = (x) => {
  console.log(x, "http");
};
</script>

<template>


  <div><Check @getPosition="getPosition" :top="top" /></div>
</template>

<style>

</style>

