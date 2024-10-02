/* 
v-on:click等於@click
if else改成show(v-show)也行，差別是show讓DOM變成displap:none，if else則完全不渲染
v-model 提供了双向数据绑定功能
*/

<template>
  <button v-on:click="changeView(1)">顯示單向綁定</button>
  <button @click="changeView(2)">顯示雙向綁定</button>
  <button @click="changeView(9999)">沒畫面</button>

  <div class="container-1" v-if="view === 1">
    <p>資料綁定 - 單向</p>
    {{ data }}
  </div>
  <div class="container-2" v-else-if="view === 2">
    <p>資料綁定 - 雙向</p>
    <input type="text" v-model="text" />
    <p>{{ text }}</p>
  </div>
  <div v-else>沒畫面</div>
</template>

<script setup>
import { ref } from "vue";

const data = "Hi React";
const text = ref("Hello Vue");
const view = ref(1);
const changeView = (index) => {
  view.value = index;
};
</script>

<style scoped>
.container-1 {
  border: 2px red solid;
}
.container-2 {
  border: 2px skyblue solid;
}
</style>
 