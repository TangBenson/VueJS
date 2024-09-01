/* 
:key的功用在於若test變數有改變，整個p標籤會刪掉重建，讓動畫再次觸發，
沒加:key就只會針對p標籤內的文字做修改，不會觸發動畫
*/
<template>
  <p v-for="text in dataList">
    {{ text }}
  </p>

  <p v-for="(value, key, index) in dataObj">
    <span v-show="key !== 'key3'"> {{ index }}.{{ key }}:{{ value }} </span>
  </p>

  <p class="test-cls" :key="test">{{ test }}</p>
</template>

<script setup>
import { ref } from "vue";

const dataList = ["a", "b", "c", "d"];
const dataObj = { key1: "A", key2: "B", key3: "C", key4: "D" };
const test = ref("test");

setTimeout(() => {
  test.value = "apple!";
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
 