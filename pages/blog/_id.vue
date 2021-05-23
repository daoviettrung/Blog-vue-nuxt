<template>
    <BlogFormEdit v-bind:idNew="idNew"></BlogFormEdit>
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