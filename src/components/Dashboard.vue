<template>
    <div id="ordemcompra-table" v-if="OrdemCompra">
      <div>
        <div id="ordemcompra-table-heading">
          <div class="order-id">#:</div>
          <div>Usuario:</div>
          <div>Fornecedor:</div>
          <div>Categoria:</div>
          <div>Produto:</div>
          <div>Unidade:</div>
          <div>Quantidade:</div>
          <div>Valor:</div>
          <div>Data:</div>
        </div>
      </div>
      <div id="ordemcompra-table-rows">
        <div class="ordemcompra-table-row" v-for="OrdemCompra in OrdemCompras " :key="OrdemCompra.id">
          <div class="order-number">{{ OrdemCompra.id }}</div>
          <div>{{ OrdemCompra.usuario }}</div>
          <div>{{ OrdemCompra.fornecedor }}</div>
          <div>{{ OrdemCompra.categoria }}</div>
          <div>{{ OrdemCompra.produto }}</div>
          <div>
            <select name="status" class="status" @change="updateOrdemCompra($event, OrdemCompra.id)">
              <option :value="s.tipo" v-for="s in status" :key="s.id" :selected="OrdemCompra.status == s.tipo">
                {{ s.tipo }}
              </option>
            </select>
            <button class="delete-btn" @click="deleteOrdemCompra(OrdemCompra.id)">Cancelar</button>
          </div>
        </div>
      </div>
    </div>
    <div v-else>
      <h2>Não há pedidos no momento!</h2>
    </div>
  </template>
  <script>
    export default {
      name: "Dashboard",
      data() {
        return {
          OrdemCompras: null,
          OrdemCompra_id: null,
          status: []
        }
      },
      methods: {
        async getPedidos() {
          const req = await fetch('http://localhost:3000/OrdemCompras')
          const data = await req.json()
          this.OrdemCompras = data
          // Resgata os status de pedidos
          this.getStatus()
        },
        async getStatus() {
          const req = await fetch('http://localhost:3000/status')
          const data = await req.json()
          this.status = data
        },
        async deleteOrdemCompras(id) {
          const req = await fetch(`http://localhost:3000/OrdemCompras/${id}`, {
            method: "DELETE"
          });
          const res = await req.json()
          this.getPedidos()
        },
        async updatOrdemCompra(event, id) {
          const option = event.target.value;
          const dataJson = JSON.stringify({status: option});
          const req = await fetch(`http://localhost:3000/OrdemCompras/${id}`, {
            method: "PATCH",
            headers: { "Content-Type" : "application/json" },
            body: dataJson
          });
          const res = await req.json()
          console.log(res)
        }
      },
      mounted () {
      this.getPedidos()
      }
    }
  </script>
  
  <style scoped>
    #ordemCompra-table {
      max-width: 1200px;
      margin: 0 auto;
    }
    #ordemcompra-table-heading,
    #ordemcompra-table-rows,
    .ordemCompra-table-row {
      display: flex;
      flex-wrap: wrap;
    }
    #ordemcompra-table-heading {
      font-weight: bold;
      padding: 12px;
      border-bottom: 3px solid #333;
    }
    .ordemcompra-table-row {
      width: 100%;
      padding: 12px;
      border-bottom: 1px solid #CCC;
    }
    #ordemcompra-table-heading div,
    .ordemcompra-table-row div {
      width: 19%;
    }
    #ordemcompra-table-heading .order-id,
    .ordemcompra-table-row .order-number {
      width: 5%;
    }
    select {
      padding: 12px 6px;
      margin-right: 12px;
    }
    .delete-btn {
      background-color: #222;
      color:#fcba03;
      font-weight: bold;
      border: 2px solid #222;
      padding: 10px;
      font-size: 16px;
      margin: 0 auto;
      cursor: pointer;
      transition: .5s;
    }
    
    .delete-btn:hover {
      background-color: transparent;
      color: #222;
    }
    
  </style>