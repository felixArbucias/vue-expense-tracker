<template>
  <Header/>
  <div class="container">
    <Balance :total="total"/>
    <IncomeExpenses :income = "income" :expenses = "expenses"/>
    <TransactionList :transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
import { ref, computed } from 'vue';

const transactions = ref([
  { id: 1, text: 'Gas', amount: -45.00},
  { id: 2, text: 'Salary', amount: 400.00},
  { id: 3, text: 'Gas', amount: -45.00},
  { id: 4, text: 'Gas', amount: -45.00},

]);
// get total
const total = computed(() => {
  return transactions.value.reduce((acc, transactions) => {
    return acc + transactions.amount;
  }, 0);
});

// get income 
const income = computed(() => {
  return transactions.value
  .filter((transactions) => transactions.amount > 0)
  .reduce((acc, transactions) => {
    return acc + transactions.amount;
  }, 0)
  .toFixed(2);
});

// get expenses
const expenses = computed(() => {
  return transactions.value
  .filter((transactions) => transactions.amount < 0)
  .reduce((acc, transactions) => {
    return acc + transactions.amount;
  }, 0)
  .toFixed(2);
});
</script>
 