/*
template第一、二個P標籤
:key的功用在於消除編譯器警告，由于Vue 3引入的严格模式。要求开发者为每个被迭代的元素提供独特的标识符

template最後一個P標籤
:key的功用在於若test變數有改變，整個p標籤會刪掉重建，讓動畫再次觸發，
沒加:key就只會針對p標籤內的文字做修改，不會觸發動畫
*/
<template>
  <p v-for="text in dataList" :key="text.id">{{ text }}</p>
  
  <h2>------------</h2>
  
  <p v-for="(value, key, index) in dataObj" :key="index">
    <span v-show="key !== 'key3'"> index值 : {{ index }}, key值 : {{ key }}, value值 : {{ value }} </span>
  </p>
  
  <h2>------------</h2>
  
  <p class="test-cls" :key="test">{{ test }}</p>
</template>

<script setup>
import { ref } from "vue";

const dataList = ["a", "b", "c"];
const dataObj = { myKey1: "RO", myKey2: "龍族", myKey3: "天下無雙", myKey4: "天堂" };

const test = ref("apple");
setTimeout(() => {
  test.value = "Nvidia !";
}, 2000);
</script>

<style scoped>
.test-cls {
  font-size: 40px;
  animation: openIn 1s ease-in-out;
}

@keyframes openIn {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
 