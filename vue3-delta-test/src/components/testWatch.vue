/*
v-model 提供了雙向數據绑定功能

watch可以監看變數的改變
watch預設監聽物件下第一層，除非設定 deep:true，但這樣回傳會變成 Proxy(響應式物件)

ref和 reactive功能相近，但 reactive用於物件會較方便(也只能用於物件)，
而 ref建議是搭配單純的輸入例如純文字使用
*/
<template>
  <input type="text" v-model="text" /><br/>
  <input type="text" v-model="textobj.levels.text" /><br/>
  <input type="text" v-model="textobj2.levels.text" /><br/>
  <input type="text" v-model="textobj2.label" />
</template>

<script setup>
import { reactive, ref, watch } from "vue";

const text = ref("");
watch(text, (newData, oldData) => {
  console.log(newData, oldData);
});

const textobj = ref({
  levels: {
    text: "",
  },
});
watch(
  () => textobj.value.levels.text,
  (newData, oldData) => {
    console.log(newData, oldData);
  },
  { deep: true }
);

const textobj2 = reactive({
  levels: {
    text: "",
  },
  label: "前綴",
});
watch(
  [() => textobj2.levels.text, () => textobj2.label],
  (newData, oldData) => {
    console.log(newData, oldData);
  }
);
</script>

<style scoped>
</style>
 