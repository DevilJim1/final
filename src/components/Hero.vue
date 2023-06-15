<script setup>
</script>

<template>
  <div class="hero-container">
    <h1 class="content">
    TMDB Movie
    </h1>
    
  </div>
</template>

<style scoped>
.hero-container {
  position:relative;
  width:100%;
  height:75%;
  font-size: 3rem;
}

.hero-container::before {
  content: "";
  top: 0px;
  right: 0px;
  bottom: 0px;
  left: 0px;
  opacity: 0.75;
  background-image:url(../../../img/a.png);
  background-size:cover;
  position: absolute;
}

.content{
  font-family:'Times New Roman', Times, serif;
  position:relative;
  opacity:0.95 !important;
}
</style>