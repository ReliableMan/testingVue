<template>

  <div v-if="lists.length > 0">
  <table class="table">

	<thead>
		<tr>
			<th @click="$emit('sort', list)">Имя</th>
			<th @click="$emit('sortNum', list)">Телефон</th>
		</tr>
	</thead>

<transition-group name="user-list">
	<tbody 
  v-for="list in lists" 
  :key="list.id" 
  @remove="$emit('remove', list)" 
  @sort="$emit('sort', list)" 
  @sortNum="$emit('sortNum', list)">

		<tr >
      
      <td> {{list.userName}}
      <table v-if="list.userMain" id="table2">
        <tr>
          <td>Начальник: {{list.userMain}}</td>
        </tr>
      </table>
      
      </td>
      
			<td>{{list.userNumber}} 

      <button-delete 
      @click="$emit('remove', list)">
      </button-delete>
      </td>


		</tr>
    <!-- <tr > 
      <h5>hey</h5>
    </tr> -->

	</tbody>
  </transition-group>

</table>
</div>

<h3 v-else style="color:teal">
    Нет контактов
    </h3>

</template>

<script>
import BtnDelete from '@/components/UI/Button-delete';
export default {
  components: { BtnDelete },
  props: {
    lists: {
      type: Array,
      required: true
    }
  },
}
</script>

<style scoped>

.table {
	width: 400px;
	margin-top: 20px;
	border: 2px solid teal;
	border-collapse: collapse; 
}

.table th {
	font-weight: bold;
	padding: 5px;
	background: #efefef;
	border: 1px solid #dddddd;
  cursor: pointer;
}

.table td {
	border: 1px solid #dddddd;
	padding: 5px;
} 

.user-list-item {
  display: inline-block;
  margin-right: 10px;
}

.user-list-enter-active,
.user-list-leave-active {
  transition: all 0.6s ease;
}

.user-list-enter-form,
.user-list-leave-to {
  opacity: 0;
  transform: translateX(150px)
}

.user-list-move {
  transition: transform 1s;
}

</style>
