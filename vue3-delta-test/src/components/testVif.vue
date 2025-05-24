/*
v-on:click等於@click
if else改成show(v-show)也行，差別是show讓DOM變成display:none，if else則完全不渲染
v-model 提供了雙向數據绑定功能，好像是用在input標籤裏頭的，讓我輸入的值即時顯示在畫面上其它欄位
*/

<template>
  <br>
  <button v-on:click="changeView(1)">顯示單向綁定</button>
  <button @click="changeView(2)">顯示雙向綁定</button>
  <button @click="changeView(9999)">沒畫面</button>

  <div class="container-1" v-if="view === 1">
    <p>資料綁定 - 單向</p>
    <p> {{ data }}</p>
  </div>
  <div class="container-2" v-else-if="view === 2">
    <p>資料綁定 - 雙向</p>
    <input type="text" v-model="text"/>
    <p>{{ text }}</p>
  </div>
  <div v-else>沒畫面</div>
</template>

<script setup>
import {ref} from "vue";

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
 