<template>

    <div class="ordemcompra-container">

        <Message />
        <form id="ordemcompra-form" @submit="createPedido">

            <div class="input-container" >
                <label for="usuario">Nome do Usuario:</label>
                <input type="text" id="usuario" name="usuario" v-model="usuario" placeholder="Digite o nome do usuario">
            </div>

            <div class="input-container">
                <label for="fornecedor">Nome do Fornecedor:</label>
                <select name="fornecedor" id="fornecedor" v-model="fornecedor">
                    <option value="">Selecione o Fornecedor</option>
                    <option v-for="fornecedor in fornecedores" :key="fornecedor.id" 
                    :value="fornecedor.tipo">
                    {{ fornecedor.tipo }}</option>                 
                </select>
            </div>

            <div class="input-container">
                <label for="categoria">Escolha uma Categoria :</label>
                <select name="categoria" id="categoria" v-model="categoria">
                    <option value="">Selecione a categoria</option>
                    <option v-for="categoria in categorias" :key="categoria.id" 
                    :value="categoria.tipo">
                    {{ categoria.tipo }}</option>                 
                </select>
            </div>

            <div class="input-container">
                <label for="produto">Selecione o Produto:</label>
                <select name="produto" id="produto" v-model="produto">
                    <option value="">Selecione a Produto</option>
                    <option v-for="produto in produtos" :key="produto.id" 
                    :value="produto.tipo">
                    {{ produto.tipo }}</option>                     
                </select>
            </div>

            <div class="input-container">
                <label for="unidade">Insira a Unidade:</label>
                <input type="text" id="unidade" name="quantidade" v-model="unidade" placeholder="Insiera a unidade">
            </div>

            <div class="input-container">
                <label for="quantidade">Insira a Quantidade:</label>
                <input type="number" id="quantidade" name="quantidade" v-model="quantidade" placeholder="Digite a quantidade do produto">
            </div>

            <div class="input-container">
                <label for="valor">Valor Unitário:</label>
                <input type="number" id="valor" name="valor" v-model="valor" placeholder="Digite o valor unitário  R$">
            </div>

            <div class="input-container">
                <label for="data">Data do Pedido:</label>
                <input type="text" id="data" name="data" v-model="data" placeholder="Digite a data do pedido">
            </div>

            <div class="input-container">
                <input type="submit" class="submit-btn" value="Gerar Ordem de Compra">
            </div>
        </form>
    </div>


</template>

<script>
import Message from './Message.vue';

    export default {
    name: "PedidoForm",
    data() {
        return {
            fornecedores: null,
            categorias: null,
            produtos: null,
            unidade: null,
            usuario: null,
            quantidade: null,
            ValorUnt: null,
            DataPedido: null,
            status: "Solicitado",
            msg: null,
        };
    },
    methods: {
        async getListItens() {
            const req = await fetch("http://localhost:3000/ListItens");
            const data = await req.json();
            this.fornecedores = data.fornecedores;
            this.categorias = data.categorias;
            this.produtos = data.produtos;
        },
        async createPedido(e) {
            e.preventDefault();
            let data = {
                usuario: this.usuario,
                fornecedor: this.fornecedor,
                categoria: this.categoria,
                produto: this.produto,
                unidade: this.unidade,
                quantidade: this.quantidade,
                valor: this.valor,
                data: this.data,
                staus: "Solicitado"
            };
            let dataJson = JSON.stringify(data); // transformando dado em texto
            let req = await fetch("http://localhost:3000/OrdemCompra", {
                method: "POST",
                headers: { "Content-type": "application/json" },
                body: dataJson
            });
            let res = await req.json();
            //colocar msg de sistema
            //limpar dados para enviar proximo pedido     
            this.fornecedor = "";
            this.categoria = "";
            this.produto = "";
            this.unidade = "";
            this.quantidade = "";
            this.valor = "";
            this.data = "";
            console.log(res);
        }
    },
    mounted() {
        this.getListItens();
    },
    components: { Message }
}

</script>

<style scoped>

#ordemcompra-container {

    background: gray;
    filter: opacity(60%);
    background-position: 0 -350px;
    background-size: cover;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
 }   

#ordemcompra-form{
    max-width: 400px;
    margin: 0 auto;
}

.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 10px;
}

label{
    font-weight: bold;
    margin-bottom: 8px;
    color: rgba(2, 2, 2, 0.925);
    padding: 5px 5px;
    border-left: 4px solid #FCBA03;
}

input, select {
    padding:5px 5px;
    width: 300px;   
}

.submit-btn{
    background-color: #222;
    color:#FCBA03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
   
    cursor:pointer;
    transition: .5s;
}

.submit-btn:hover{
    background: transparent;
    color:#222;
}
</style>