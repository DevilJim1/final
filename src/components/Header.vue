<script setup>
import { useRouter } from "vue-router";
import { auth } from "../firebase/index.js";
import { 
  signOut 
} from 'firebase/auth'

const router = useRouter();

const moveLogin = () => {
    router.push("./login");
};

const moveCart = () => {
    router.push("./cart");
};

const moveHome = () => {
  router.push("./account")
}

const moveRegister = () => {
  router.push("./register")
}

const logout = async () => {
  await signOut(auth)
  router.push('/login')
}
const props = defineProps({
  lon : Boolean,
});

</script>

<template>
<div class="grid-container">
<div class="item">
    <p id="logo">TMDB</p>
</div>
<div class="grid-item">
    <p v-if="!lon"/>
    <button id="logout" @click="logout" v-if="lon" >Log Out</button>
</div>
<div class="grid-item">
    <button id="login" @click="moveLogin" v-if="!lon" >Login</button>
    <button id="home" @click="moveHome" v-if="lon" >Home</button>
</div>
<div class="grid-item">
  <button id="register" @click="moveRegister" v-if="!lon">Register</button>
  <button id="cart" @click="moveCart" v-if="lon">Cart</button>
</div>
</div>
</template>

<style scoped>
.grid-container {
  position:absolute;

  display: grid;
  grid-template-columns: 2fr 6fr 2fr 2fr;
  width:100vw;
  height:10%;

  color: black;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  background-color:rgb(197, 27, 189);
  font-size: 3rem;

  margin-top:0;
  padding-top:0;

  top:5px;
}

#logout {
  width:80px;
}

#logo {
  margin-top:0;
  padding-top:0;
  padding-left:20px;

  height:40px;
  width:auto;
}

.grid-item {
  background-color: rgb(197, 27, 189);
  font-size: 30px;
  text-align: center;
  height:50px;
  width:auto;
}

</style>