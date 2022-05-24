<template>

  <form @submit.prevent>
    <p class="subtitle"> Добавление пользователя</p>

    <div class="input1">
      <label class="label-text">Имя</label>
        <my-input v-model="list.userName" type='text'/>
    </div>

    <div class="input1">
        <label class="label-text">Номер</label>
        <my-input v-model="list.userNumber" type='text'/>
    </div>

    <div class="input1">
        <label class="label-text">Начальник</label>
        <check-box v-model="list.userMain"></check-box>
    </div>
        <my-button @click="createUser">Сохранить</my-button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      list: {
        userName: '',
        userNumber: '',
        userMain: ''
      }
    }
  }, 
  methods: {
    createUser() {
      this.list.id = Date.now();
      this.$emit('create', this.list)
      this.list = {
        userName: '',
        userNumber: '',
        userMain: ''
      }
    }
  },
}
</script>

<style scoped>

form {
  display: flex;
  flex-direction: column;
}

.input1{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-content: center;
  margin-bottom: 10px
}

.subtitle{
  margin-top: 5px;
  font-size: 25px;
  color:aliceblue
}

.label-text{
  font-size: 20px;
  color:aliceblue
}


</style>
