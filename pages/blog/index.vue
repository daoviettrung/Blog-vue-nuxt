<template>
  <div class="list-blog">
    <BlogList
      v-bind:dataList="listBlog"
      v-on:callBackDataDelete="callBackDataDelete"
    ></BlogList>
  </div>
</template>
<script>
export default {
  data() {
    return {
      listBlog: [],
    }
  },
  async fetch() {
    await fetch('http://localhost:81/api-conn-vue/public/api/blog')
      .then((res) => res.json())
      .then((res) => {
        this.listBlog = res.data
      })
  },

  methods: {
    async callBackDataDelete(){
       const dataNew = await this.$axios.$get("http://localhost:81/api-conn-vue/public/api/blog");
       this.listBlog = dataNew.data
    },
  },
}
</script>