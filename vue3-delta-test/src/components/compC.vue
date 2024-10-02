/*
使用computed會自動判斷若num的值改變才會觸發numFormat
但若是用一般function實作，則第一個input選數字時也會觸發numFormat2

官方建議computed做純計算就好，不要去打api
*/

<template>
  <h1>Computed 計算屬性</h1>
  <h6>~ ~ 請開console看log ~ ~</h6>

  <input type="number" v-model="num0" />
  <br /><br />
  <input type="number" v-model="num" />
  <h3>Computed版 : {{ numFormat }}</h3>
  <h3>一般版 : {{ numFormat2() }}</h3>

  <input type="text" v-model="fullName" />
  <p>{{ firstName }}</p>
  <p>{{ lastName }}</p>
</template>

<script setup>
import { computed, ref } from "vue";

// 範例一:做計算
const num0 = ref(0);
const num = ref(0);
const numFormat = computed(() => {
  console.log("change");
  if (Number.isNaN(num.value * 100)) return num.value;
  return `${num.value * 100}%`;
});
const numFormat2 = () => {
  console.log("change");
  if (Number.isNaN(num.value * 100)) return num.value;
  return `${num.value * 100}%`;
};

// 範例二:動資料
const firstName = ref("John");
const lastName = ref("Fee");
const fullName = computed({
  get() {
    return `${firstName.value} ${lastName.value}`;
  },
  set(newName) {
    const [newfirst, newlast] = newName.split(" ");
    firstName.value = newfirst;
    lastName.value = newlast;
  },
});
</script>

<style scoped>
</style>
 