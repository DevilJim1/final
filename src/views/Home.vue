<script setup>
import Header from "../components/Header.vue";
import Hero from "../components/Hero.vue";
import Footer from "../components/Footer.vue";

</script>

<template>
  <div class="home-container">
  <Header v-bind:lon="false" />
  <Hero/>
  <Footer/>
  </div>
</template>

<style scoped>
body {
  width:100vw;
}
.home-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  
  background-color:rgb(197, 27, 189);

  top:0;
}
header {
  margin:0;
  padding:0;
}

form {
  display: flex;
  flex-direction: column;
}
</style>