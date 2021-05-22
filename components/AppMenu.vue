
<template>
  <div class="sidenav">
    <a class="text-dark ml-4 mt-3"><NuxtLink to="/blog"><i class="fa fa-list" aria-hidden="true"></i> List
    </NuxtLink></a>
    <a class="text-dark ml-4 mt-3"><NuxtLink to="/blog/create"><i class="fa fa-plus-square-o" aria-hidden="true"></i> New
    </NuxtLink>
    </a>
    <a class="text-dark ml-4 mt-3"><NuxtLink to="/blog/create"><i class="fa fa-search" aria-hidden="true"></i> Search
    </NuxtLink></a>
    <i class="fas fa-list"></i>
  </div>
</template>

<script>
export default {}
</script>

<style>
.sidenav {
    height: 95%;
    width: 300px;
    position: fixed;
    top: 0;
    left: 0;
    background-color: white;
    margin-top: 69px;
  }
  
  .sidenav a {
    padding: 6px 8px 6px 16px;
    text-decoration: none;
    font-size: 1em;
    color: #818181;
    display: block;
  }
  
  .sidenav a:hover {
    color: black;
  }
  
  
  @media screen and (max-height: 450px) {
    .sidenav {padding-top: 15px;}
    .sidenav a {font-size: 18px;}
  }
</style>
