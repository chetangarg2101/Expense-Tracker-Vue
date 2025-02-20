<template>
    <div>
      <h2>Expense List</h2>
      <ul>
        <li v-for="(expense, index) in expenses" :key="index">
          <span>{{ expense.name }} - ${{ expense.amount.toFixed(2) }}</span>
          <button @click="deleteExpense(index)">Delete</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      expenses: Array
    },
    methods: {
      deleteExpense(index) {
        this.$emit('delete-expense', index);
      }
    }
  }
  </script>
  