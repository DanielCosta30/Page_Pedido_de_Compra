<template>
  
  <div class="main-container">
    <h1>Ordem de Compra</h1>
    <PedidoForm />


  </div>
  </template>
  
  <script>
import PedidoForm from '@/components/PedidoForm.vue';
    

    export default {
    name: "OrdemCompra",
    components: { PedidoForm }
}

  </script>