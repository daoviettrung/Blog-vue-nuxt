<template>
  <div class="list-blog">
    <BlogSearchData v-on:resultSearch="dataSearchs"></BlogSearchData>
    <BlogList v-bind:dataList="listBlog"></BlogList>
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
    this.listBlog = await fetch('http://localhost:3000/blogs').then((res) =>
      res.json()
    )
  },
  methods: {
    async dataSearchs(dataSearch) {
      const result = await this.$axios.$get(
        'http://localhost:3000/blogs?title_like=' + dataSearch
      );
      this.listBlog = result;
    },
  },
}
</script>
