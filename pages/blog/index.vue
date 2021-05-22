<template>
<div class="list-blog">
  <BlogList v-bind:dataList="listBlog"></BlogList>
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
}
</script>