<template>
  <div class="tabbar" id="app">
    <p>请输入数字</p>
    <input v-model="currentValue">
    <Item :value="currentValue"></Item>
    <div></div>
  </div>
</template>
<script>
import Item from "./components/HelloWorld";

let count = 0;
export default {
  components: {
    Item
  },
  data: function () {
    return {
      currentValue: 12,
      add2: '',
      test1: '',
      test2: '',
      add: '',
      add1: '',
      add3: ''
    };
  },
};

</script>

<style>

</style>
