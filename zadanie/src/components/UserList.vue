<template>
  <div v-if="lists.length > 0">
  <table class="table">
	<thead>
		<tr>
			<th>Имя</th>
			<th>Телефон</th>
		</tr>
	</thead>

	<tbody v-for="list in lists" :key="list.id" @remove="$emit('remove', list)">
		<tr>
      <td>{{list.userName}}</td>
			<td>{{list.userNumber}} 
      <button-delete @click="$emit('remove', list)"></button-delete>
      </td>

		</tr>
	</tbody>
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
  }
}
</script>

<style scoped>
.table {
	width: 50%;
	margin-top: 20px;
	border: 2px solid teal;
	border-collapse: collapse; 
}
.table th {
	font-weight: bold;
	padding: 5px;
	background: #efefef;
	border: 1px solid #dddddd;
}
.table td {
	border: 1px solid #dddddd;
	padding: 5px;
} 
</style>
