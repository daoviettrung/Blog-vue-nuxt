<template>
  <div class="list-blog">
    <BlogSearchData v-on:resultSearch="dataSearchs"></BlogSearchData>
    <BlogList v-bind:style="marginT" v-bind:dataList="listBlog"></BlogList>
  </div>
</template>
<style>
</style>
<script>
import axios from 'axios'
export default {
  
  data() {
    return {
      marginT : 'margin-top : 15px',
      listBlog: [],
    }
  },
    async fetch() {
    await fetch("http://localhost:81/api-conn-vue/public/api/blog").then((res) =>
      res.json()
    ).then ((res) =>{
      this.listBlog = res.data
    });
  },
  methods: {
    async dataSearchs(dataSearch) {
      axios
        .get("http://localhost:81/api-conn-vue/public/api/blog" + '/' + dataSearch)
        .then((response) => (this.listBlog = response.data.data))
    },
  },
}
</script>
