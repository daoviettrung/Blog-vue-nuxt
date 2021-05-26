<template>
  <div class="create-blog">
    <BlogCreateEdit v-bind:flagCheckisCreate ="flagCheckisCreate"></BlogCreateEdit>
  </div>
</template>

<script>
export default {
    data(){
        return {
           flagCheckisCreate : 1
        }
    },
}
</script>
<style scoped>
.create-blog{
    margin-top: 50px;
}
</style>