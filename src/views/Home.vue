<script setup>
// DEPENDENCIES
import { ref, onMounted, onBeforeMount } from "vue";
import axios from "axios";
// COMPONENTS
import RegisterUser from "../components/RegisterUser.vue";
import TableUsers from "../components/TableUsers.vue";
const title = ref("Usuarios");
</script>

<template>
  <div class="home">
    <div class="bg"></div>
    <div class="bg bg2"></div>
    <div class="bg bg3"></div>
    <div class="container">
      <h1 class="title">{{ title }}</h1>
      <div class="panel">
        <RegisterUser />
        <TableUsers />
      </div>
    </div>
  </div>
</template>

<style scoped>
.bg {
  animation: slide 7s ease-in-out infinite alternate;
  background-image: linear-gradient(-45deg, rgb(0, 31, 111) 50%, #09f 50%);
  bottom: 0;
  left: -50%;
  opacity: 0.5;
  position: fixed;
  right: -50%;
  top: 0;
  z-index: -1;
}

.bg2 {
  animation-direction: alternate-reverse;
  animation-duration: 9s;
}

.bg3 {
  animation-duration: 11s;
}

@keyframes slide {
  0% {
    transform: translateX(-25%);
  }
  100% {
    transform: translateX(25%);
  }
}
.container {
  text-align: center;
}
.title {
  font-size: 3em;
  margin: 20px 0;
}
.panel {
  display: flex;
  flex-wrap: wrap;
}
.panel .register-form {
  flex: 1;
}
.panel > .user-table {
  flex: 2;
}

.card-wrapper {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 20px;
  padding: 20px;
  z-index: 1;
  box-shadow: 20px 20px 50px rgba(0, 0, 0, 0.5);
  border-radius: 15px;
  border-top: 1px solid rgba(255, 255, 255, 0.5);
  border-left: 1px solid rgba(255, 255, 255, 0.5);
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(5px);
  overflow: hidden;
}
@media (max-width: 800px) {
  .panel {
    flex-direction: column;
  }
  .card-wrapper {
    margin: 20px;
  }
}
</style>
