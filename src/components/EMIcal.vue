<template>
  <form @submit.prevent="calculate">
    <div>
      <label>loan amount</label>
      <input v-model.number="loanAmount" />
    </div>
    <div>
      <label>interest rate</label>
      <input v-model.number="interestRate" />
    </div>
    <div>
      <label>number of months to pay off loan</label>
      <input v-model.number="numMonths" />
    </div>
    <button type="submit">calculate monthly payment</button>
  </form>
  <p>monthly payment: {{ monthlyPayment.toFixed(2) }}</p>
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