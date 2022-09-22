<template>
    
<div id="main-banner">
    <h1>SAFE VALUE</h1>

</div>

</template>

<script>

    export default{
        name:"Banner"
    }


</script>

<style scoped>
 #main-banner {
    background: url('/public/img/bg.jpg') no-repeat center center;
    filter: opacity(60%);
    background-position: 0 -350px;
    background-size: cover;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
 }

#main-banner h1{
  font-size: 50px;
  text-align: center;
  margin-bottom: 30px;
  background-color: #2222;
  padding: 20px 40px;
}
</style>

