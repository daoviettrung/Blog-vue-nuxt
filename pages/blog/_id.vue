<template>
    <BlogCreateEdit v-bind:idNew="idNew"></BlogCreateEdit>
</template>
<script>
export default {
    data(){
        return {
           idNew : "",
        }
    },
    mounted(){
        this.idNew = this.$route.params.id;
    }
}
</script>