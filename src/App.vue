<script setup>
import { ref } from 'vue'
const produtos = ref([
  {
    id: 1,
    nome: 'Camiseta da nike',
    preco: 49.90,
    quantidade: 0
  },
  {
    id: 2,
    nome: 'Calça da nike',
    preco: 99.90,
    quantidade: 0
  },
  {
    id: 3,
    nome: 'Meia da nike',
    preco: 9.90,
    quantidade: 0
  },
  {
    id: 4,
    nome: 'tenis da nike',
    preco: 199.90,
    quantidade: 0
  },
  {
    id: 5,
    nome: 'Boné da nike',
    preco: 29.90,
    quantidade: 0
  },
  {
    id: 6,
    nome: 'Óculos juliete',
    preco: 99.90,
    quantidade: 0
  },
  {
    id: 7,
    nome: 'Relógio de ouro',
    preco: 299.90,
    quantidade: 0
  },
  {
    id: 8,
    nome: 'Bermuda da nike',
    preco: 79.90,
    quantidade: 0
  },
  {
    id: 9,
    nome: 'Cueca do ben 10',
    preco: 19.90,
    quantidade: 0
  },
  {
    id: 10,
    nome: 'Meia da nike',
    preco: 9.90,
    quantidade: 0
  }
]
)
let valorTotal = ref(0)

const carrinho = ref({
  items: [],
  total: 0
})

// Função adicionar carrinho
function adicionarCarrinho(produto) {
  carrinho.value.items.push({
    id: produto.id,
    nome: produto.nome,
    preco: produto.preco,
    quantidade: produto.quantidade,
    total: produto.preco * produto.quantidade
  });
  carrinho.value.total += produto.preco * produto.quantidade
}
// Função adicionar item
function mais(index) {
  produtos.value[index].quantidade++
  const pos = carrinho.value.items.indexOf(carrinho.value.items.find(c => c.id === produtos.value[index].id))
  if (pos != -1) {
    carrinho.value.total -= carrinho.value.items[pos].total
    carrinho.value.items[pos].total = ++carrinho.value.items[pos].quantidade * carrinho.value.items[pos].preco
    carrinho.value.total += carrinho.value.items[pos].total

  }
}
function menos(index) {
  produtos.value[index].quantidade--
}
</script>

<template>
<div class="titulo">
   <h1>COMPRAS DE CRIA</h1>
    </div>
  <div class="template">


    <div v-for="(produto, index) in produtos" :key="produto.id" class="col-3">

      <div class="produtos">
        <b id="negrito"> {{ produto.id }} - {{ produto.nome }}</b>
      <br>
      <b id="negrito"> {{ produto.preco }} R$</b>
      <br>
      <b id="negrito"> {{ produto.quantidade }} </b>
      <br><button type="button" @click="menos(index)" class="btn bg-danger p-2 h-r">-</button>
      <button type="button" @click="mais(index)" class="btn bg-danger p-2 ml-b h-g">+</button>
      <button type="button" @click="adicionarCarrinho(produto)" class="btn bg-danger p-2 ml-b h-g">Adicionar</button>
      </div>
    </div>
  </div>


      
      <button type="button" class="btn btn-primary p-3 mt-2 " data-bs-toggle="modal" data-bs-target="#exampleModal">
    Carrinho
    </button>
    <hr>
   
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h1 class="modal-title fs-5" id="exampleModalLabel">Carrinho</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <div v-for="(itemDoCarrinho, index) in carrinho.items" :key="itemDoCarrinho.id">
            <strong> {{ itemDoCarrinho.id }} - {{ itemDoCarrinho.nome }}</strong>
            <br>
            <p>Preço R$ {{itemDoCarrinho.preco }} | Quant {{ itemDoCarrinho.quantidade}} (Total: {{ itemDoCarrinho.total }} )</p>

          </div>
          <p v-if="carrinho.length > 0">Valor total da compra: R$ {{ carrinho.total }}</p>
          <p v-else>Nenhum item no carrinho</p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fechar</button>
            
          </div>
        </div>
      </div>
    </div>
</template>


<style scoped>
.template {
  background-color: black;
  border-radius: 15px;
  box-shadow: 10px 10px 10px 10px;
  border: 100px wheat;
  display: flex  ;
  flex-direction: row;
  flex-wrap: wrap;
  
  

}

h1 {
  color: brown;
  padding-top: 40px;
  text-align: center;
  text-decoration: underline;
}

#negrito {
  color: rgb(187, 46, 46);
}

.ml-b {
  margin-left: 7px;

}
.titulo{
  background-color: black;
  border-radius: 15px;
  box-shadow: 10px 10px 10px 10px;
  border: 100px wheat;
  
    
}
</style>
