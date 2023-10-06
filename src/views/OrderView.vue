<script setup>
import Myheader from '../components/Myheader.vue';
import { orders } from '../stores/order_cal';
import { computed } from 'vue';

const totalPrice = (item) => computed(() => item.quantity * item.price);

const totalItemsInOrder = (order) => {
  return order.items.reduce((accum, item) => accum + item.quantity, 0);
};

const totalOrderPrice = (order) => {
  return order.items.reduce((accum, item) => accum + item.quantity * item.price, 0);
};
</script>

<template>
  <Myheader></Myheader>
  <div>
    <h1 style="margin-top: 25px; text-align: center; font-size: 50px; font-weight: 400;">
      Coffee Shop website
    </h1><hr style="margin-bottom: 40px;">
  </div>

    <div v-if="orders.list.length">
      <div class="container_all" v-for="(order) in orders.list" :key="order.id">
        <div style="margin-left: 150px; margin-right: 150px;">
          <h1 class="m-3" style="font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif; font-size: 40px; font-weight: 400;">ประวัติการสั่งซื้อ</h1>
        </div>

        <div style="padding-left: 150px; padding-right: 150px;">
          <div style="background-color: #ffffff; height: 100%; padding-left: 70px; padding-right: 70px; padding-top: 10px; padding-bottom: 30px; border-radius: 10px;">

            <div class="">
              <h2 class="" style="font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif; font-size: ; font-weight: 400;">คำสั่งซื้อที่ : {{ order.id }}</h2>
            </div>

            <div style="background-color: ; border-radius: 10px;">
            <div class="card" v-for="(item,index) in order.items" :key="index">
              <div class="grid-container">

                <div style="display: grid; justify-items: center; align-items: center; padding: 10px;">
                  <img :src="item.coverimage" :alt="name" style="width:100%; border-radius: 10px;">
                </div>

                <div class="container" style="display: grid; text-align: center; justify-items: center; align-items: center; margin-top: 40px; margin-bottom: 40px;">
                  <span style="font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif; font-size: 20px;">รายการ {{ index + 1 }} </span>
                  <h3><b>{{ item.name }}</b></h3>
                  <p style="font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif; font-size: 20px;">ราคา : {{ item.price }} $</p>
                </div>

                <div class="container-quantity" style="display: grid; justify-items: center; align-items: center;">
                  <input id="form1" min="0" name="quantity" type="number" v-model="item.quantity" class="form-control form-control-sm" style="height: 30px; border-radius: 5px; width: 100px; padding-left: 10px;"/>
                </div>

                <div class="container-price" style="display: grid; justify-items: center; align-items: center;">
                  <h2 style="font-size: 26px; font-weight: 400;">{{ totalPrice(item).value }} บาท</h2>
                </div>

                <div class="" style="display: grid; justify-items: center; align-items: center;">
                  <button @click="() => removeFromCart(item)" class="">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" style="fill: rgba(0, 0, 0, 1);transform: ;msFilter:;">
                      <path d="M6 7H5v13a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V7H6zm4 12H8v-9h2v9zm6 0h-2v-9h2v9zm.618-15L15 2H9L7.382 4H3v2h18V4z"></path>
                    </svg>
                  </button>
                </div>

              </div>
              </div>
            </div>

            <div class="card mb-5">

                  <p class="list-all" style="margin-bottom: -20px;">
                    <h1 style="font-weight: 500; text-align: end;"><span>รายการทั้งหมด {{ totalItemsInOrder(order) }} จำนวน </span></h1>
                  </p>

                  <p class="total-price">
                    <strong><h1 style="font-size: 36px; font-weight: 500; text-align: end;"><span>ยอดรวมทั้งหมด {{ totalOrderPrice(order) }}  บาท</span></h1></strong>
                  </p>

            </div>

          </div>
        </div>
      </div>
    </div>

    <div v-else>
      <p style="display: grid; justify-items: center; margin-top: 300px; color: red; font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif; font-size: 40px; font-weight: 400;">**ไม่มีรายการคำสั่งซื้อ**</p>
    </div>

</template>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  /*grid-column-gap: 0px;
  grid-row-gap: 0px;*/
}

h2, h3 {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
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