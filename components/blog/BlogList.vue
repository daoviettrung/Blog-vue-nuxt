<template>
  <div id="form-list" class="card mr-4">
    <div class="card-header">
      <h3>List Blog</h3>
    </div>
    <div class="card-body">
      <table id="table">
        <tr>
          <th>Id</th>
          <th>Tin</th>
          <th>Loại</th>
          <th>Trạng thái</th>
          <th>Vị trí</th>
          <th>Ngày</th>
          <th>Edit</th>
          <th>Delete</th>
        </tr>
        <tbody>
          <tr v-for="data in dataList" :key="data.id" v-bind:data="data">
            <td>{{ data.id }}</td>
            <td>{{ data.title }}</td>
            <td>{{ getNameCate(data.category) }}</td>
            <td>{{ data.public }}</td>
            <td>{{ getNamePositions(data.position) }}</td>
            <td>{{ data.data_pubblic }}</td>
            <td>
              <a class="btn btn-outline-primary"
                ><NuxtLink :to="`/blog/${data.id}`">Edit</NuxtLink></a
              >
            </td>

            <td>
              <a @click="deleteData(data.id)" class="btn btn-outline-danger"
                >Delete</a
              >
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="card-footer"></div>
  </div>
</template>
<script>
import { API, CATEGORIES, POSITIONS } from 'assets/constans'
export default {
  props: {
    dataList: Array,
  },
  methods: {
    async deleteData(id) {
      if (confirm('Do you want to delete?')) {
        this.$axios.$delete(API +"/"+ id).then(() => {
          this.dataList
        })
        this.$emit('callBackDataDelete');
      }
    },
    getNameCate(id) {
      var cate = CATEGORIES.find((category) => {
        return category.id == id
      })
      return cate && cate.name
    },
    getNamePositions: function (id) {
      var namePosi = ''
      for (var i in POSITIONS) {
        if (POSITIONS[i].id == id) {
          namePosi = POSITIONS[i].name
        }
      }
      return namePosi
    },
    
  },
}
</script>
<style>
#form-list {
  margin-top: 80px;
}

table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  margin-left: -20px;
  margin-right: -30px;
  width: 103%;
  height: 100%;
}

.card-header {
  height: 60px;
}

h3 {
  text-align: left;
  margin-top: 10px;
  color: black;
}
td,
th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}
#form-list.card-body {
  margin-top: -100px;
}
.card-body table {
  margin-top: -20px;
  margin-bottom: -20px;
}
</style>
