// * строим разметку, шаблон 
<template>    
<div class='app'>
  <div class="header">
    <my-button @click="showModal">Добавить</my-button>
  </div>
  <my-modal v-model:show="modalVisible">
    <user-form  @create="createUser"/>
  </my-modal>
  <user-list :lists="lists" @remove="removeUser"/>
</div>

</template>

// *  логика, функции, данные
<script>
import UserForm from "@/components/UserForm";
import UserList from "@/components/UserList"
import MyButton from './components/UI/MyButton.vue';


export default {
  components: {
    UserForm, UserList,
    MyButton
  },
  data() {
    return {
      lists: [
        {id: 1, userName: "Nastya", userNumber: "+7 941 532 56 87" },
        {id: 2, userName: "Anastasya", userNumber: "+7 943 532 59 87" },
        {id: 3, userName: "Stasya", userNumber: "+7 944 532 50 87" }
      ],
      modalVisible: false,
    }
  },
  methods: {
    createUser(user) {
      this.lists.push(user);
      this.modalVisible = false;
    },
    removeUser(list) {
      this.lists = this.lists.filter(l => l.id !== list.id )
    }, 
    showModal() {
      this.modalVisible = true;
    }
  },
}
</script>

<style>

.app {
  padding: 15px
}

.header{
  display: flex;
  justify-content: center;
}

</style>
