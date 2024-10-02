/* 
:data 就是 v-bind:data
ref可以讓變數被監聽，有變化就一起變
*/

<template>
  <button @click="changeView(1)" class="container">v-if</button>
  <button @click="changeView(2)" class="container">v-for</button>
  <button @click="changeView(3)" class="container">computed</button>
  <button @click="changeView(4)" class="container">watch</button>
  <button @click="changeView(5)" class="container">child</button>

  <div v-if="view === 0"><h3>歡迎來到 Vue3 新手村</h3></div>
  <br />
  <div v-if="view === 1"><compAVue /></div>
  <div v-if="view === 2"><compBVue /></div>
  <div v-if="view === 3"><compCVue /></div>
  <div v-if="view === 4"><compDVue /></div>
  <div v-if="view === 5">
    <div style="background-color: yellow">
      <h5>此行位於App.vue組件，輸入的值會帶到Child.vue</h5>
      <input type="text" v-model="msg" />
    </div>
    <div style="background-color: pink"><Child :data="msg" @update="updateHandler" /></div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import compAVue from "./components/compA.vue";
import compBVue from "./components/compB.vue";
import compCVue from "./components/compC.vue";
import compDVue from "./components/compD.vue";
import Child from "./components/Child.vue";

const view = ref(0); // ref => 当该值发生变化时，Vue 会检测到变化并更新相关的视图
const changeView = (index) => {
  view.value = index;
};

const msg = ref("");
const updateHandler = (data) => {
  console.log(data);
};
</script>

<style scoped>
.container {
  border: 2px greenyellow solid;
}
</style>
 