<template>
  <h2>Balance: <span :class ="totalClass">{{total}}</span></h2>
</template>

<script>

export default {
  name: 'TotalBalance',
  props: {
    total: {
      type: Number,
      default: 0,
    },
  },

  computed: {
    totalClass() {
      if (this.total > 0) {
        return 'positive';
      } if (this.total < 0) {
        return 'negative';
      }
      return 'zero';
    },
  },

};
</script>


<style scoped>
.positive{
  color: green;
}
.negative{
  color: red;;

}
.zero{
  color: black;
}
</style>
