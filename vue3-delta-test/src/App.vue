/* 
:data 就是 v-bind:data
ref可以讓變數被監聽，有變化就一起變
*/

<template>
  <div class="fixed-top">
    這是固定在最上方的內容
  </div>
  <button v-on:click="changeView(1)" class="container">v-if</button>
  <button @click="changeView(2)" class="container">v-for</button>
  <button @click="changeView(3)" class="container">computed</button>
  <button @click="changeView(4)" class="container">watch</button>
  <button @click="changeView(5)" class="container">child</button>
  <button @click="changeView(6)" class="container">組件生命週期</button>
  <button @click="changeView(0)" class="container">重置</button>

  <div v-if="view === 0"><h3>歡迎來到 Vue3 新手村</h3></div>
  <br />
  <div v-if="view === 1"><compVif /></div>
  <div v-if="view === 2"><compVFor /></div>
  <div v-if="view === 3"><compComputed /></div>
  <div v-if="view === 4"><compWatch /></div>
  <div v-if="view === 5">
    <div style="background-color: palevioletred">
      <h5>此區塊位於App.vue組件，輸入的值會帶到Child.vue</h5>
      <input type="text" v-model="msg" />
    </div>
    <div style="background-color: pink">
      <Child :data="msg" @update="updateHandler" />
    </div>
    <div style="background-color: palevioletred">
      <h5>此區塊位於App.vue組件，呈現子組件傳給父組件的訊息</h5>
      {{ msgFromChild }}
    </div>
  </div>
  <div v-if="view === 6">
    <button @click="showLife = !showLife">toggle</button>
    <br />
    <compLife v-if="showLife" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import compVif from "./components/testVif.vue";
import compVFor from "./components/testVFor.vue";
import compComputed from "./components/testComputed.vue";
import compWatch from "./components/testWatch.vue";
import Child from "./components/Child.vue";
import compLife from "./components/testLifeCircle.vue";
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";

const view = ref(0); // ref => 當該值發生變化時，Vue 會檢測到變化並更新相關的視圖
const changeView = (index) => {
  view.value = index;
};

const msg = ref("");
const msgFromChild = ref("");
// 實作子傳父而定義的 function
const updateHandler = (data) => {
  msgFromChild.value = data;
  console.log(data);
};

// 生命週期
const showLife = ref(true);

onBeforeMount(() => {
  // 掛載前
  console.log("app: before mount");
});
onMounted(() => {
  // 已掛載，一直處於此狀態，組件有任何更新會觸發Update，卸載會觸發Unmounted
  console.log("app: Mounted");
});
onBeforeUpdate(() => {
  console.log("app: before Update");
});
onUpdated(() => {
  console.log("app: Updated");
});
onBeforeUnmount(() => {
  console.log("app: before Unmount");
});
onUnmounted(() => {
  console.log("app: Unmounted");
});
</script>

<style scoped>
.container {
  border: 2px greenyellow solid;
}
</style>
 