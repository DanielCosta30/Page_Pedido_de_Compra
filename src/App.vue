<template>

  <NavB :logo="logo_src" :alt="app_name" />
  <router-view/>
  <Footer />

</template>

<script>
// parando em 3:10min do video #22 e alterado css
import NavB from './components/NavB.vue';
import Footer from './components/Footer.vue';

export default{
    components: {
    NavB,
    Footer
},
data(){
  return {
    logo_src: "/img/LogoCar.png",
    app_name: "Make Your Burger"
  }
}
}
</script>


<style>
 *{

    font-family: Helvetica, sans-serif;
    padding:0;
    margin:0;
    box-sizing: border-box;
  }

.main-container {
  margin:50px;
  min-height:250px;

}
h1 {
  font-size: 24px;
  text-align: center;
  margin-bottom: 30px;
  
}


</style>
