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
  data: function() {
    return {
      currentValue: 12,
      test2:''
    };
  },
};

</script>

<style>

</style>
