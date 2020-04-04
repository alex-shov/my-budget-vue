<template>
  <div class="wrap">
    <h4>Budget List</h4>
    <ul v-if="list.length > 0">
      <li v-for="(item, index) in list" :key="index">
        <img v-if="item.type === 'INCOME'" src="../assets/up-arrow.svg" alt="">
        <img v-else src="../assets/download-arrow.svg" alt="">
        <span class="comment">{{ item.comment }} {{ index }}</span>
        <span :class="[item.type === 'INCOME' ? 'income' : 'outcome', 'value']">
          {{ item.value }}
        </span>
        <button @click="deleteItem(item.id)">Delete</button>
      </li>
    </ul>
    <p v-else>Расходов и доходов не имеется</p>
  </div>
</template>

<script>
export default {
  name: 'BudgetList',
  props: ['list'],
  methods: {
    deleteItem(id) {
      // eslint-disable-next-line no-alert
      // eslint-disable-next-line no-restricted-globals
      const deleteConfirm = confirm('Удалить это изменение бюджета?');
      if (deleteConfirm) {
        this.$emit('deleteItem', id);
        // eslint-disable-next-line no-useless-return
      } else return;
    },
  },
};
</script>

<style scoped>
.wrap {
  width: 500px;
  border: 1px solid #ccc;
  margin: 0 auto;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
}
h4 {
  text-align: center;
}
ul {
  padding: 0;
  margin: 30px 0 0 0;
}
li {
  list-style: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 20px 20px 20px;
}
img{
  width: 14px;
  margin-right: 5px;
  stroke: red;
}

.comment::first-letter {
  text-transform: uppercase;
}
.value {
  margin: 0 20px 0 auto;
  font-weight: bold;
}
.income {
  color: green;
}
.outcome {
  color: red;
}
button {
  padding: 7px 15px;
  font-size: 12px;
  background-color: #f56c6c;
  border: #f56c6c;
  border-radius: 3px;
  color: #fff;
  cursor: pointer;
}
</style>
