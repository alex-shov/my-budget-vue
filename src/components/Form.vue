<template>
  <form @submit.prevent="onSubmit">
    <label><span>Type</span>
    <select v-model='formData.type' name="" id="">
      <option>INCOME</option>
      <option>OUTCOME</option>
     </select>
    </label>

<label><span>Comments</span>
<input type="text" v-model="formData.comment" required>
</label>

<label><span>Value</span>
<input type="number" v-model.number.trim="formData.value" required>
</label>

<input type="submit" value="Submit" />
  </form>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return ({
      formData: {
        type: 'INCOME',
        comment: '',
        value: 0,
      },
    });
  },
  methods: {
    onSubmit() {
      this.formData.id = Math.random();
      console.log(this.formData);
      this.$emit('onSubmit', { ...this.formData }); // Передаём копию объекта, а не сам объект
      this.formData.comment = '';
      this.formData.value = 0;
    },
  },

};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  width: 500px;
  border: 1px solid #ccc;
  margin: 0 auto;
  padding: 20px 30px 20px;
  box-shadow: 0 2px 12px 0 rgba(0,0,0,.1);
}
select, input{
  border-radius: 3px;
  outline: 0;
  border: 1px solid #ccc;
}
select{
  width: 100%;
}
select{
  padding: 7px;
}
label{
  font-size: 16px;
  text-align: left;
  margin-bottom: 30px;
}
span{
  display: block;
  margin-bottom: 10px;
}
input{
  width: 100%;
  padding: 7px;
}
input[type='submit']{
  background-color: #409EFF;
  border: 1px solid #409EFF;
  color: #fff;
  border-radius: 3px;
  width: 25%;
  margin: auto;
  cursor: pointer;
}
</style>
