<template>
  <div class="list-blog">
    <BlogList v-bind:dataList="listBlog" v-on:onDelete="onDelete"></BlogList>
  </div>
</template>
<script>
export default {
  data() {
    return {
      listBlog: [],
    }
  },
  methods: {
    async reloadDate() {
      await fetch('http://localhost:81/api-conn-vue/public/api/blog')
        .then((res) => res.json())
        .then((res) => {
          this.listBlog = res.data
        })
    },
    async onDelete() {
      this.reloadDate()
    },
  },
  mounted(){
    this.reloadDate()
  }
}
</script>