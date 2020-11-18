<template>
  <Navbar @model-show="modelToggle" />
  <Model @model-toggle="modelToggle" :status="modelStatus" @store-expense="storeExpense" />
  <Expenses :allExpenses="expenses" />
</template>

<script>
import Navbar from './components/Navbar.vue'
import Model from './components/Model.vue'
import Expenses from './components/Expenses.vue'
export default {
  name: 'App',
  components: {
    Navbar,
    Model,
    Expenses,
  },

  data() {
    return {
      modelStatus: false,
      expenses: {
        balance: 0,
        income: 0,
        expense: 0,
        history: []
      }
    }
  },

  methods: {
    modelToggle() {
      /**true ko false kro and vice versa */
      this.modelStatus = !this.modelStatus
    },

    storeExpense(payload) {
      const number = parseInt(payload.number);
      if(number>1){
        this.expenses = {
          ...this.expenses,
          income: this.expenses.income + number,
          balance: this.expenses.balance + number,
          history: [{title: payload.title, number}, ...this.expenses.history],
        };
      }else if(number < 1){
        this.expenses = {
          ...this.expenses,
          expense: this.expenses.expense + number,
          balance: this.expenses.balance + number,
          history: [{title: payload.title, number}, ...this.expenses.history],
        };
      }
      this.modelStatus = false;
    }
  },
}
</script>

<!-- * means it'll target all the html tags -->
<style>

* {
  margin: 0;
  padding:0;
  box-sizing: border-box;
}

body{
  background: #fafafa;
  font-family: sans-serif;
}

</style>
