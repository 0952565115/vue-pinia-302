<template>
  <div class="card" v-for="(i,index) in shop_food" :key="index">
    <img :src="i.coverimage" :alt="name" style="width:100%; border-radius: 10px 10px 0px 0px;">
    <div class="container">
      <h2 style="font-size: 26px; margin-bottom: -15px;"><b>{{ i.name }}</b></h2>
      <p style="font-size: 20px;">ราคา : {{ i.price }} $</p>

      <p class="card-text">
        <button class="btn btn-primary" type="submit" @click="handleAddToCart(i)" style="text-align: center;">เพิ่มลงตะกร้า</button>
      </p>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { menuStore } from '../stores/All_menu';
import { addToCart } from '../stores/counter';

const allmenu = menuStore();
const shop_food = ref(allmenu.menu_list);

const handleAddToCart = (item) => {
  addToCart(item);
};
</script>

<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.6s;
  margin: 30px;
  border-radius: 10px;
  background-color: white;
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
  padding: 10px;
}
.container {
  padding: 10px 25px;
}

h2, h3 {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}
.card-text {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.btn {
  text-align: center;
  width: 120px;
  height: 40px;
  font-size: 16px;
  border-radius: 10px;
  background-color: lightblue;
  border: 0;
}
.btn:hover {
  color: white;
  background-color: lightcoral;
  transition: 0.6s;
  border: 0;
}
</style>