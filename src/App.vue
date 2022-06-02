<script setup>
import Home from "./views/Home.vue";
</script>

<template>
  <Home />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
  user-select: none;
}
*::before *::after {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
}
</style>
