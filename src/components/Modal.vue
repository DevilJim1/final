<script setup>
import axios from "axios";
import { useStore } from "../store/index.js";

const store = useStore();
const props = defineProps(["id"]);
const emits = defineEmits(["toggleModal"]);

let data = (
  await axios.get(`https://api.themoviedb.org/3/movie/${props.id}`, {
    params: {
      api_key: "64688a2ee40628130c4073aff0308684",
    },
  })
).data;
</script>

<template>
  <Teleport to="body">
    <div class="modal-outer-container" @click.self="emits('toggleModal')">
      <div class="modal-inner-container">
        <button class="close-button" @click="emits('toggleModal')">X</button>
        <div class="wrapper">
            <div class="img">
              <img :src="'https://image.tmdb.org/t/p/w500' + data.poster_path" class="image"/>
            </div>
            <div class="introduction">
              <h1>{{ data.title }}</h1>
              Original Title - {{ data.original_title }} <br /><br/>
              Release Date: {{ data.release_date }} <br /><br/>
              Overview: {{ data.overview }}<br /><br/>
              <button @click="store.addToCart(props.id, {
              id: data.id,
              poster: data.poster_path,
              title: data.title,
              date: data.release_date,
            })">
            Purchase
          </button>
            </div>
          </div>
      </div>
    </div>
  </Teleport>
</template>

<style scoped>
.modal-outer-container {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  background: #00000099;
  z-index: 3;
}

.modal-outer-container .modal-inner-container {
  background-color: #1F2123;
  width: clamp(280px, 100%, 800px);
  height: 400px;
  position: relative;
}

.modal-outer-container .modal-inner-container .close-button {
  position: absolute;
  right: 0px;
  padding: 1rem;
  border: none;
  background: #1F2123;
  font-weight: bold;
  font-size: 1.25rem;
  color: white;
}

.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.wrapper>.img>img {
  height: 400px;
  width: auto;
}

.wrapper>.introduction {
  color: white;
}
</style>