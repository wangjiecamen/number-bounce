<template>
  <div class="hello">
    <div>{{currentValue|num|turn}}</div>
  </div>
</template>

<script>
export default {
  props: ["value"],
  filters: {
    turn(val) {
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
    num(val) {
      return Math.round(val);
    }
  },
  data() {
    return {
      steps: 20,
      timeOut: 500,
      initValue: this.value,
      targetValue: this.value,
      currentValue: this.value,
      currentStep: 0
    };
  },
  watch: {
    value: function(oldValue, newValue) {
      this.targetValue = newValue;
      this.step();
    }
  },
  methods: {
    getValue(precent) {
      let diff = this.targetValue - this.initValue;
      return diff * precent + this.initValue;
    },
    step() {
      const that = this;
      that.currentStep = 0;
      that.initValue = that.currentValue;
      that.targetValue = that.value;
      that.interval = setInterval(function() {
        that.currentValue = that.getValue(that.currentStep / that.steps);
        that.currentStep = that.currentStep + 1;
        if (that.currentStep > that.steps) {
          clearInterval(that.interval);
        }
      }, that.timeOut / that.steps);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
