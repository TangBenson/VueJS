<template>
  <button @click="changeView(1)" class="container">v-if</button>
  <button @click="changeView(2)" class="container">v-for</button>
  <button @click="changeView(3)" class="container">computed</button>
  <button @click="changeView(4)" class="container">watch</button>

  <div v-if="view === 0">
    <h3>歡迎來到 Vue3 新手村</h3>
  </div>
  <br />
  <br />
  <br />
  <br />
  <div v-if="view === 1">
    <compAVue />
  </div>
  <div v-if="view === 2">
    <compBVue />
  </div>
  <div v-if="view === 3">
    <compCVue />
  </div>
  <div v-if="view === 4">
    <compDVue />
  </div>
</template>

<script setup>
import { ref } from "vue";
import compAVue from "./components/compA.vue";
import compBVue from "./components/compB.vue";
import compCVue from "./components/compC.vue";
import compDVue from "./components/compD.vue";

const view = ref(0);
const changeView = (index) => {
  view.value = index;
};
</script>

<style scoped>
.container {
  border: 2px greenyellow solid;
}
</style>
 