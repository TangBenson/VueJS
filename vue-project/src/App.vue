<script>
//所有程式邏輯都必須要寫在 export default {} 裡頭
export default {
  //宣告這個 .vue 的名稱
  name: "App",

  //data 是用來宣告變數的地方，將變數message輸出給 <template></template> 來使用
  data() {
    return {
      message: "Hello World",
      isShow: true,
      x: 25,
      y: 45,
      users1: ["Jake", "Allan", "Eason"],
      users2: [
        { name: "Jake", email: "jake@gmail.com" },
        { name: "Allan", email: "allan@gmail.com" },
        { name: "Eason", email: "eason@gmail.com" },
      ],
      count: 0,
      name: "嗨",
      text: '多行的輸入文字框 Textarea，AI浪潮來襲，前端工程師的未來在哪裡？',
      selectValue: '',
    };
  },
  //methods 是用來宣告函式的地方，將函式 myFunction 輸出給 <template></template> 來使用
  methods: {
    myFunction(value) {
      return this.x * this.y + value;
      //注意在這邊要用 this 來取得定義在 data() 內的變數
    },
    clickButton() {
      this.count++;
    },
  },
};
</script>

<template>
  {{ message }}
  <br />

  <!-- v-show 與 v-if 的差別在於，無法像 v-if 一樣可以寫多重的 if 判斷 -->
  <p v-if="isShow">Welcome New World</p>
  <br />

  <!-- Vue3 使用 if 判斷式是使用 v-if 這個關鍵字 -->
  <p v-if="x === 0">x = 0</p>
  <p v-else-if="x === 1">x = 1</p>
  <p v-else-if="x === 2">x = 2</p>
  <p v-else>x != 0</p>
  <br />

  <div v-for="(user, index) in users1" :key="user">
    <p v-if="user === 'Jake'">{{ index }} {{ user }}</p>
  </div>

  <p v-for="(user, index) in users2" :key="user.email">
    {{ index }} {{ user.name }} {{ user.email }}
  </p>

  {{ myFunction(100) }}
  <br />

  {{ count }}
  <button v-on:click="clickButton">按我</button><br />

  --{{ name }} <br />
  <p v-once>{{ name }}</p> <br />
  <!-- v-once 只會執行一次 -->
  <input type="text" v-model="name" />
  <!-- v-model.trim 可以去除前後空白 -->
  <!-- v-model.lazy 可以在輸入完畢將游標跳出，input 輸入框才會將值寫入到變數內 -->
  <br />

  {{ text }} <br />
  <textarea v-model="text" />
  <br />

  {{ selectValue }} <br />
  <select v-model="selectValue">
    <option value="">select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
  </select>

</template>