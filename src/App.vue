<template>
  <div id="app">
    <Header></Header>
    <router-view></router-view>
  </div>
</template>

<script>
  import Header from "./components/layout/Header";
  export default {
      name:"app",
      components:{
          Header
      },
  }
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
}

body{
  line-height: 1.4;
}

.btn{
  display: inline-block;
  border:none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover{
  background: #666;
}
</style>
