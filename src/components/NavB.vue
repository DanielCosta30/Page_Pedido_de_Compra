<template>

    <div id="nav">
      <router-link to="/" id="logo-url">
        <img id="logo" :src="logo" :alt="alt">
      </router-link>

      <router-link to="/">Home</router-link>
      <router-link to="/pedidos">Pedidos</router-link>
    </div>


</template>

<script>

export default {
        name: 'NavB',
        props:["logo", "alt"]

    }
</script>

<style scoped>

#nav{
  background-color: #c1dedc; 
  box-shadow: 0px 0px 50px 0px;
  padding: 10px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#nav #logo-url{
  margin: auto;
  margin-left: 0;
}

#logo {
  width: 50px;
  height: 50px;
}

#nav a {

  font-size: 20px;
  color: rgb(68, 68, 64);
  text-decoration: none;
  margin :12px;
  transition: .5s;

}
 #nav a:hover{
  color: rgb(134, 125, 125)
 }



</style>