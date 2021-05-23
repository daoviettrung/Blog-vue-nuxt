<template>
    <div id="blog-search" class="card">
        <div class="card-header">
            <h3>Search blog</h3>
        </div>
    <div class="card-body">
        <div class="row">
            <p class="col-md-1 ">Title: </p>
            <input placeholder="Search..." type="text" class="col-md-10" v-model="dataSearch"/>
        </div>
    <div class="submit-search">
         <button class="btn btn-outline-success my-2 text-center" 
         
         @click="searchData" >Submit</button>
    </div>
    </div>
    </div>
</template>
<script>
export default {
    data(){
        return{
            dataSearch : "",
        }
    },
    methods:{
        searchData(){
            this.$emit('resultSearch', this.dataSearch);
        }
    }
}
</script>
<style>
#blog-search{
    margin-top: 90px;
}
.card-header{
    height: 40px;
}
.submit-search{
    text-align: center;
    margin-left: 100px;
}
input{
    border: 0,7px;
}
</style>