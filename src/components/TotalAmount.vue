<template>
    <div>
      <h2>Total Amount: ${{ totalAmount.toFixed(2) }}</h2>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      expenses: Array
    },
    computed: {
      totalAmount() {
        return this.expenses.reduce((total, expense) => total + expense.amount, 0);
      }
    }
  }
  </script>
  