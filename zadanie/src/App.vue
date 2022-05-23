// * строим разметку, шаблон 
<template>    

<div class='app'>
  
  <div class="header">
    <my-button @click="showModal">Добавить</my-button>
    <!-- <my-select v-model="selectedSort" :options="sortOptions"></my-select> -->
  </div>

  <my-modal v-model:show="modalVisible">
   <user-form  @create="createUser"/>
  </my-modal>

  <user-list 
  :lists="sortedUser" 
  @remove="removeUser" 
  @sort="sorted" 
  @sortNum="sortedNum" />
</div>

</template>

// *  логика, функции, данные
<script>
import UserForm from "@/components/UserForm";
import UserList from "@/components/UserList"
import MyButton from './components/UI/MyButton.vue';
// import MySelect from './components/UI/MySelect.vue';


export default {
  components: {
    UserForm, UserList,
    MyButton,
    // MySelect
  },
  data() {
    return {
      lists: [],
      modalVisible: false,
      selectedSort: '',
      sortOptions: [
        {value: 'userName', name: 'По имени'},
        {value: 'userNumber', name: 'По номеру'}
      ]
    }
  },
  methods: {
    createUser(user) {
        this.lists.push(user);
        localStorage.setItem('user', JSON.stringify(this.lists));
        this.modalVisible = false;
    },
    removeUser(list) {
      this.lists = this.lists.filter(l => l.id !== list.id );
      localStorage.setItem('user', JSON.stringify(this.lists))
    }, 
    showModal() {
      this.modalVisible = true;
    },
    sorted() {
      this.lists.sort((a, b) => a.userName.localeCompare(b.userName))
    },
    sortedNum() {
       this.lists.sort((a, b) => a.userNumber.localeCompare(b.userNumber) )
    }
  },
  mounted() {
   const data = localStorage.getItem('user');
   data ? this.lists = JSON.parse(data) : null;
  }, 
 computed: {
   sortedUser(){
     return [...this.lists].sort((user1, user2) => {
       return user1[this.selectedSort]?.localeCompare(user2[this.selectedSort])
     })
   }
 }
}
</script>

<style>

.app {
  padding: 15px
}

.header{
  display: flex;
  justify-content: flex-start;
}

</style>
