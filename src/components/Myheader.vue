<template>
  <div class="Myheader">
    <ul style="width: 100%;">
      <li><img src="https://www.emojiall.com/en/header-svg/%E2%98%95%EF%B8%8F.svg" alt="" style="width: 30px; margin-left: 20px; margin-right: 0px; margin-top: 10px;"></li>
      <li><p>Coffee Shop website</p></li>
      <li><a class="active" href="/">Home</a></li>
      
      <div class="group">
        <li>
          <router-link :to="{ name: 'cart' }">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" style="fill: rgb(255, 255, 255);transform: ;msFilter:;">
              <path d="M21 4H2v2h2.3l3.28 9a3 3 0 0 0 2.82 2H19v-2h-8.6a1 1 0 0 1-.94-.66L9 13h9.28a2 2 0 0 0 1.92-1.45L22 5.27A1 1 0 0 0 21.27 4 .84.84 0 0 0 21 4zm-2.75 7h-10L6.43 6h13.24z"></path><circle cx="10.5" cy="19.5" r="1.5"></circle><circle cx="16.5" cy="19.5" r="1.5"></circle>
            </svg>
            <span> {{ totalItems }} </span>
          </router-link>
        </li>
        <li>
          <router-link :to="{ name: 'orderview' }">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" style="fill: rgb(255, 255, 255);transform: ;msFilter:;">
                <path d="m21.484 7.125-9.022-5a1.003 1.003 0 0 0-.968 0l-8.978 4.96a1 1 0 0 0-.003 1.748l9.022 5.04a.995.995 0 0 0 .973.001l8.978-5a1 1 0 0 0-.002-1.749z"></path><path d="m12 15.856-8.515-4.73-.971 1.748 9 5a1 1 0 0 0 .971 0l9-5-.971-1.748L12 15.856z"></path><path d="m12 19.856-8.515-4.73-.971 1.748 9 5a1 1 0 0 0 .971 0l9-5-.971-1.748L12 19.856z"></path>
            </svg>
          </router-link>
        </li>
      </div>

    </ul>
  </div>

</template>

<script setup>
import {  computed } from 'vue';
import { cart } from '../stores/counter';


const totalItems = computed(() => cart.value.reduce((acc, item) => acc + item.quantity, 0));
</script>

<style scoped>

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
}

li {
  float: left;
}

li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li p {
  display: block;
  color: white;
  text-align: center;
  text-decoration: none;
  margin-top: 14px;
  margin-left: 25px;
  margin-right: 15px;
}

li a:hover {
  background-color: #111;
}

</style>