<script setup>
import Myheader from '../components/Myheader.vue';
import Mylist from '../components/Mylist.vue';

</script>

<template>
  <main>
    <Myheader></Myheader>
    <div>
      <h1 style="margin-top: 25px; text-align: center; font-size: 50px; font-weight: 400;">
          Coffee Shop website
      </h1><hr>
    </div>
    <div class="grid-container">
      <Mylist></Mylist>
    </div>
  </main>
</template>

<style scoped>
.grid-container {
  display: grid;
  /*grid-column-gap: 0px;
  grid-row-gap: 0px;*/
}

@media (min-width: 576px) {
  .grid-container { grid-template-columns: repeat(1, 1fr);
  margin-left: 75px;
  margin-right: 75px;
  }
}

@media (min-width: 768px) {
  .grid-container { grid-template-columns: repeat(2, 1fr);
  margin-left: 75px;
  margin-right: 75px;
  }
}

@media (min-width: 992px) {
  .grid-container { grid-template-columns: repeat(2, 1fr);
  margin-left: 75px;
  margin-right: 75px;
  }
}

@media (min-width: 1200px) {
  .grid-container { grid-template-columns: repeat(3, 1fr);
  margin-left: 100px;
  margin-right: 100px;
  }
}

@media (min-width: 1400px) {
  .grid-container { grid-template-columns: repeat(3, 1fr);
  margin-left: 150px;
  margin-right: 150px;
  }
}
</style>