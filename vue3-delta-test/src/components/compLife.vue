<template>
Component Life
</template>

<script setup>
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  ref
} from "vue";


// 生命週期
onBeforeMount(()=>{
  // 掛載前
  console.log('life: before mount')
})
onMounted(()=>{
  // 已掛載，一直處於此狀態，組件有任何更新會觸發Update，卸載會觸發Unmounted
  console.log('life: Mounted')
})
onBeforeUpdate(()=>{
  console.log('life: before Update')
})
onUpdated(()=>{
  console.log('life: Updated')
})
onBeforeUnmount(()=>{
  console.log('life: before Unmount')
})
onUnmounted(()=>{
  console.log('life: Unmounted')
})
</script>