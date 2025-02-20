<template>
    <div>
      <h2>Add Expense</h2>
      <form @submit.prevent="submitForm">
        <input v-model="name" type="text" placeholder="Expense Name" required />
        <input v-model="amount" type="number" placeholder="Amount" required min="0" />
        <button type="submit">Add Expense</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        amount: ''
      };
    },
    methods: {
      submitForm() {
        if (this.name.trim() && this.amount > 0) {
          const newExpense = {
            name: this.name,
            amount: parseFloat(this.amount)
          };
          this.$emit('add-expense', newExpense);
          this.name = '';
          this.amount = '';
        } else {
          alert('Please enter a valid expense name and amount!');
        }
      }
    }
  }
  </script>
  