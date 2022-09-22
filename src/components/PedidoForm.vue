<template>

    <div>
        <p>Componente de Mensagem</p>
        <form id="ordemcompra-form">

            <div class="input-container">
                <label for="usuario">Nome do Usuario:</label>
                <input type="text" id="usuario" name="name" v-model="usuario" placeholder="Digite o nome do usuario">
            </div>

            <div class="input-container">
                <label for="fornecedor">Nome do Fornecedor:</label>
                <select name="forn" id="forn" v-model="fornecedor">
                    <option value="">Selecione o Fornecedor</option>
                    <option value="Cometa">Supermecado Cometa</option>                 
                </select>
            </div>

            <div class="input-container">
                <label for="categoria">Escolha uma Categoria :</label>
                <select name="cat" id="cat" v-model="categoria">
                    <option value="">Selecione a categoria</option>
                    <option value="Limpeza">Limpeza</option>                 
                </select>
            </div>

            <div class="input-container">
                <label for="produto">Selecione o Produto:</label>
                <select name="prod" id="prod" v-model="produto">
                    <option value="">Selecione a Produto</option>
                    <option value="produto">Carne Fraldinha</option>                 
                </select>
            </div>

            <div class="input-container">
                <label for="unidade">Selecione a unidade:</label>
                <select name="und" id="und" v-model="unidade">
                    <option value="">Selecione a unidade</option>
                    <option value="Kg">Kg</option>                 
                </select>
            </div>

            <div class="input-container">
                <label for="quantidade">Insira a Quantidade:</label>
                <input type="number" id="quantidade" name="quantidade" v-model="quantidade" placeholder="Digite a quantidade do produto">
            </div>

            <div class="input-container">
                <label for="valor">Valor Unitário:</label>
                <input type="number" id="valor" name="name" v-model="valor" placeholder="Digite o valor unitário  R$">
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

    export default {
        name:"PedidoForm"
    }

</script>