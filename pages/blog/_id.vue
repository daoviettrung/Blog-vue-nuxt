<template>
    <BlogCreateEdit v-bind:idNew="idNew"
    v-bind:flagCheckisCreate =" flagCheckisCreate"
    ></BlogCreateEdit>
</template>
<script>
export default {
    data(){
        return {
           idNew : "",
           flagCheckisCreate : 2
        }
    },
    mounted(){
        this.idNew = this.$route.params.id;
    }
}
</script>