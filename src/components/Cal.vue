<template>
  <section>
    <input placeholder="num1" type="number" v-model.number="num1" />
    <select v-model="operand">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <input placeholder="num2" type="number" v-model.number="num2" />
    <h2>{{ result() }}</h2>
  </section>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operand: "",
    };
  },
  methods: {
    result() {
      switch (this.operand) {
        case "+":
          return this.num1 + this.num2;
        case "-":
          return this.num1 - this.num2;
        case "*":
          return this.num1 * this.num2;
        case "/":
          return this.num1 / this.num2;
      }
    },
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
