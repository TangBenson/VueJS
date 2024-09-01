<script setup>
import { ref, onMounted } from "vue";
const count = ref(0);

const increment = () => {
  count.value++;
};
onMounted(() => {
  console.log(`The initial count is ${count.value}.`);
});

// import { ref, onMounted } from "vue";
// export default {
//   setup() {
//     const count = ref(0);

//     const increment = () => {
//       count.value++;
//     };
//     onMounted(() => {
//       console.log(`The initial count is ${count.value}.`);
//     });
//     return { count, increment };
//   },
// };

// export default {
//   data() {
//     return {
//       count: 0,
//     };
//   },
//   methods: {
//     increment() {
//       this.count++;
//     },
//   },
//   mounted() {
//     console.log(`The initial count is ${this.count}.`);
//   },
// };
</script>

<template>
  <div>
    <h1>Vue: {{ count }}</h1>
    <button @click="count++">Count is: {{ count }}</button>
  </div>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>