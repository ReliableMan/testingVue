<template>

  <div id="v-model-select" >
  <select class="demo" v-model="selected">
    <option disabled value=""> Выберите в списке ниже </option>
    <option v-for="main in users" :key="main.id"> {{main.userName}}
    </option>
  </select>
</div>

</template>

<script>
export default {
  name: "check-box",
  
  data() {
    return {
      selected: '',
      users: [...JSON.parse(localStorage.getItem('user'))]
    }
  },
}
console.log('---', localStorage.getItem('user'))
</script>

<style scoped>

.demo{
  height: 25px;
  font-size: 15px;
  padding-right: 12px;
  padding-left: 12px;
}

</style>
