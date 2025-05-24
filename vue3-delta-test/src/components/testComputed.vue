/*
computed 用來做資料預處理，讓api給的資料便可用

使用computed會自動判斷若num的值改變才會觸發numFormat
但若是用一般function實作，則第一個input選數字時也會觸發numFormat2

官方建議computed做純計算就好，不要去打api
*/

<template>
  <h6>~ ~ 範例一 : 請看console log ~ ~</h6>

  輸入文字:<input type="text" v-model="str" /><br>
  輸入數字<input type="number" v-model="num" />
  <h3>Computed版 : {{ numFormat }}</h3>
  <h3>一般版 : {{ numFormat2() }}</h3>

  <h6>~ ~ 範例二 ~ ~</h6>
  
  <input type="text" v-model="fullName" />
  <p>{{ firstName }}</p>
  <p>{{ lastName }}</p>
</template>

<script setup>
import { computed, ref } from "vue";

// 範例一:做計算
const str = ref('Cool');
const num = ref(0);

// computer計算的變數異動才會觸發
const numFormat = computed(() => {
  console.log("change numFormat");
  if (Number.isNaN(num.value * 100)) return num.value;
  return `${num.value * 100}%`;
});

// 畫面更新就會執行
const numFormat2 = () => {
  console.log("change numFormat2");
  if (Number.isNaN(num.value * 100)) return num.value;
  return `${num.value * 100}%`;
};

// 範例二:動資料
const firstName = ref("John");
const lastName = ref("Wick");
const fullName = computed({
  get() {
    return `${firstName.value} ${lastName.value}`;
  },
  set(newName) {
    const [newFirst, newLast] = newName.split(' ');
    firstName.value = newFirst;
    lastName.value = newLast;
  },
});
</script>

<style scoped>
</style>
 