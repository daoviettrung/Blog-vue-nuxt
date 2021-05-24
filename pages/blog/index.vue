<template>
<div class="list-blog">
  <BlogList v-bind:dataList="listBlog"
  v-on:callBackDataDelete="callBackDataDelete"
  ></BlogList>
</div>
</template>
<script>
export default {
    data() {
    return {
      listBlog: [],
    };
  },
    async fetch() {
    this.listBlog = await fetch("http://localhost:3000/blogs").then((res) =>
      res.json()
    );
  },

  methods:{
    async callBackDataDelete(){
       const dataNew = await this.$axios.$get("http://localhost:3000/blogs");
       this.listBlog = dataNew
    }
  }
}
</script>