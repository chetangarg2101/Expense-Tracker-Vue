<template>
  <div id="app">
    <div class="container">
      <h1>Expense Tracker</h1>
      <ExpenseForm @add-expense="addExpense" />
      <ExpenseList :expenses="expenses" @delete-expense="deleteExpense" />
      <TotalAmount :expenses="expenses" />
    </div>
  </div>
</template>

<script>
import ExpenseForm from './components/ExpenseForm.vue'
import ExpenseList from './components/ExpenseList.vue'
import TotalAmount from './components/TotalAmount.vue'

export default {
  name: 'App',
  components: {
    ExpenseForm,
    ExpenseList,
    TotalAmount
  },
  data() {
    return {
      expenses: JSON.parse(localStorage.getItem('expenses')) || []
    };
  },
  methods: {
    addExpense(expense) {
      this.expenses.push(expense);
      localStorage.setItem('expenses', JSON.stringify(this.expenses));
    },
    deleteExpense(index) {
      this.expenses.splice(index, 1);
      localStorage.setItem('expenses', JSON.stringify(this.expenses));
    }
  }
}
</script>

<style>
#app {
  font-family: 'Arial', sans-serif;
  background-color: #f5f5f5;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #333;
}

.container {
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 350px;
  padding: 20px;
  text-align: center;
  color: #333;
}

h1 {
  font-size: 24px;
  color: inherit;
  margin-bottom: 20px;
}

button {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #45a049;
}

input {
  padding: 10px;
  margin: 10px 0;
  width: 80%;
  border-radius: 4px;
  border: 1px solid #ccc;
}

input:focus {
  outline: none;
  border-color: #4CAF50;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  background-color: #f2f2f2;
  padding: 10px;
  margin: 5px 0;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li span {
  font-size: 16px;
}

li button {
  background-color: #ff4d4d;
  font-size: 14px;
}

li button:hover {
  background-color: #e60000;
}

h2 {
  font-size: 18px;
  color: inherit;
}
body.dark-theme #app {
  background-color: #333;
  color: #f5f5f5; /* Light text for dark theme */
}

body.dark-theme .container {
  background-color: #444; /* Dark background for the container */
  color: #f5f5f5; /* Light text for dark theme */
}

body.dark-theme button {
  background-color: #4CAF50;
  color: #fff;
}

body.dark-theme input {
  border: 1px solid #ccc;
  background-color: #555; /* Dark background for input */
  color: #f5f5f5; /* Light text for input */
}

body.dark-theme li {
  background-color: #666; /* Dark background for list items */
  color: #f5f5f5; /* Light text for list items */
}

body.dark-theme li button {
  background-color: #ff4d4d;
  color: #fff;
}
</style>
