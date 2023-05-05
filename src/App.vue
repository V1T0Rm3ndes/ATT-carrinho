<script setup>
const produtos = [
    {
        id: 1,
        nome: 'Camiseta da nike',
        preco: 49.90
    },
    {
        id: 2,
        nome: 'Calça da nike',
        preco: 99.90
    },
    {
        id: 3,
        nome: 'Meia da nike',
        preco: 9.90
    },
    {
        id: 4,
        nome: 'tenis da nike',
        preco: 199.90
    },
    {
        id: 5,
        nome: 'Boné da nike',
        preco: 29.90
    },
    {
        id: 6,
        nome: 'Óculos juliete',
        preco: 99.90
    },
    {
        id: 7,
        nome: 'Relógio de ouro',
        preco: 299.90
    },
    {
        id: 8,
        nome: 'Bermuda da nike',
        preco: 79.90
    },
    {
        id: 9,
        nome: 'Cueca do ben 10',
        preco: 19.90
    },
    {
        id: 10,
        nome: 'Meia da nike',
        preco: 9.90
    }
]

const carrinho = [
    {
        id: 1,
        nome: 'Camiseta da nike',
        preco: 49.90,
        quantidade: 1,
        valorTotal: 49.90
    },
    {
        id: 2,
        nome: 'Calça da nike',
        preco: 99.90,
        quantidade: 2,
        valorTotal: 199.80
    },
    {
        id: 3,
        nome: 'Meia da nike',
        preco: 9.90,
        quantidade: 4,
        valorTotal: 39.60
    }
  
]

</script>

<template>

  <div class="template">
    <h1>COMPRAS DE CRIA</h1>

    <div v-for="(produtos,id) in produtos" :key="id">
    <b id="negrito"> {{ produtos.id}} - {{ produtos.nome }}</b>
    </div>


  </div>


</template>


<style scoped>
.template{
  background-color: black;
  border-radius: 15px;
  box-shadow: 10px 10px 10px 10px;
  border: 100px  wheat;
 
  
  
}
h1{
  color: brown;
  padding-top: 40px;
  text-align: center;
}

#negrito{
    color: brown;
}

</style>
