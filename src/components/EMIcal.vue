<template>
  <form @submit.prevent="calculate">
    <div>
      <label class="label success">Loan amount</label>
      <input v-model.number="loanAmount" />
    </div>
    <div>
      <label class="label info">Interest rate</label>
      <input v-model.number="interestRate" />
    </div>
    <div>
      <label class="label warning">Number of months to pay off loan</label>
      <input v-model.number="numMonths" />
    </div>
    <button class="button" type="submit">Calculate monthly payment</button>
  </form>
  <p><label class="label danger"> monthly payment: {{ monthlyPayment.toFixed(2) }}</label></p>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      loanAmount: 0,
      interestRate: 0,
      numMonths: 0,
      monthlyPayment: 0,
    };
  },
  computed: {
    formValid() {
      const { loanAmount, interestRate, numMonths } = this;
      return (
        +loanAmount >= 0 &&
        0 <= +interestRate &&
        +interestRate <= 100 &&
        +numMonths > 0
      );
    },
  },
  methods: {
    calculate() {
      if (!this.formValid) {
        return;
      }
      const { loanAmount, interestRate, numMonths } = this;
      this.monthlyPayment = (loanAmount * (1 + interestRate / 100)) / numMonths;
    },
  },
};
</script>


<style>


.label {
  width:180px;
  height: 100px;
  clear:left;
  color: white;
  padding-right: 10px;
  font-family: Arial;
  text-align:left;
   font-weight: bold;
  line-height: 40px;
}
.success {background-color: #04AA6D;} /* Green */
.info {background-color: #2196F3;} /* Blue */
.warning {background-color: #ff9800;} /* Orange */
.danger {background-color: #f44336;} /* Red */ 
.other {background-color: #e7e7e7; color: black;} /* Gray */ 
.button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  font-weight: bold;
  line-height: 40px;
}
</style>