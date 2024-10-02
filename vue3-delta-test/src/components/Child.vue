<template>
  <h5>此行位於Child.vue組件</h5>
  <div>字數:{{ msgCount }}</div>
  <!-- {{ data }} -->
</template>

<script setup>
import { computed } from "@vue/reactivity";
import { watch } from "vue";

// 簡化版 - 該語法糖定義組件(Child.vue)接收哪些外部資料(App.vue)
// defineProps(['data']);

// 正常版
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

// msgCount改變的值會放到 newValue 裡面
watch(msgCount, (newValue) => {
  emit("update", newValue);
});
</script>

<style>
</style>
