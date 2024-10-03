<template>
  <h5>此區塊位於Child.vue組件，呈現父組件傳遞的訊息</h5>
  {{ data }}
  <div>字數:{{ msgCount }}</div>
</template>

<script setup>
import { computed } from "@vue/reactivity";
import { watch } from "vue";

// 簡化版 - 該語法糖定義組件(Child.vue)接收哪些外部資料(App.vue)
// defineProps(['data']);

// 正常版 (物件的方式，可定義資料長相)
const props = defineProps({
  data: {
    type: String,
    default: "",
    // ....等其它功能
  },
});

const msgCount = computed(() => {
  return props.data.length;
});

// 定義子組件哪些事件可以發出去
const emit = defineEmits(["update"]);

// 子組件發出update事件時一併攜帶newValue給父組件
watch(() => props.data[props.data.length - 1], (newValue) => {
  emit("update", `傳給父的: ${newValue}`);
});
</script>

<style>
</style>
