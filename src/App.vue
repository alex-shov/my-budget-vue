/* eslint-disable no-console */
<template>
  <div id="app">
    <Form @onSubmit="formSubmit" />
    <TotalBalance :total="totalBalance" />
    <BudgetList :list="list" @deleteItem="onDelete" />
  </div>
</template>

<script>
import BudgetList from './components/BudgetList.vue';
import TotalBalance from './components/TotalBalance.vue';
import Form from './components/Form.vue';

export default {
  name: 'App',
  components: {
    BudgetList,
    TotalBalance,
    Form,
  },
  data: () => ({
    list: [
      {
        type: 'INCOME',
        comment: 'some comment INCOME',
        value: 100,
        id: 0,
      },
      {
        type: 'OUTCOME',
        comment: 'other some comment OUTCOME',
        value: 50,
        id: 1,
      },
    ],
  }),
  methods: {
    onDelete(id) {
      let newlist = [];
      newlist = this.list.filter((item) => item.id !== id);
      this.list = newlist;
    },
    formSubmit(formData) {
      this.list.unshift(formData);
      console.log(this.list);
    },
  },
  computed: {
    totalBalance() {
      let itog = 0;
      for (let i = 0; i < this.list.length; i += 1) {
        if (this.list[i].type === 'INCOME') {
          itog += this.list[i].value;
        } else {
          itog -= this.list[i].value;
        }
      }
      // const incomeArr = this.list.filter((item) => item.type === 'INCOME');
      // const incomeArrSum = incomeArr.reduce

      return itog;
    },
  },
};
</script>

<style lang="scss">
#app {
  * {
    box-sizing: border-box;
  }

  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
