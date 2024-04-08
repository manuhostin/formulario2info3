<script setup>
import { reactive, ref } from 'vue'

const titulo = ref('Título')
const mostrarResultado = ref(false) 
const produto = reactive({
  nome: 'produto 1',
  preco : 0 ,
  quantidade : 10,
  categorias : []
})
function formatarpreco (preco) {
  return `R$ ${preco.toFixed(2).replace('.', '.')}`
}
</script>

<template>
  <h1>{{ titulo }}</h1>
  <div class="container">
    <div class="formulario">
      <h1>Formulario</h1>
      <input type="text" v-model="titulo">
      <form @submit.prevent="mostrarResultado = !mostrarResultado">
      <div class="row">
        <label for="">Nome:</label>
        <input type="text" v-model="produto.nome" required >
      </div>
      <div class="row">
        <label for="">Preco:</label>
        <input type="number" v-model="produto.preco"/>
      </div>
      <div class="row">
        <label for="">Quantidade:</label>
        <input type="number" v-model="produto.quantidade"/>
      </div>
      <button type="submit">Mostrar</button>
    </form>
    </div>
    <div v-if="mostrarResultado" class="resultado">
      <h1>Resultado</h1>
      <p>Nome: {{ produto.nome }}</p>
      <p>preco: {{ formatarpreco(produto.preco) }}</p>
      <p>quantidade: {{ produto.quantidade }}</p>
      <p>categorias: {{ produto.categorias }}</p>
      <P> {{ mostrarResultado }}</P>
    </div>
  </div>
</template>

<style scoped>

.container{
  display: flex;
  flex-direction: row;
  gap: 1.5rem ;
  width: 100vw;
}

.formulario, .resultado{
  width: 45%;
  border-radius: 10px;
  padding: 10px;
}

.formulario{
  background-color: #c4c500;
}

.formulario .row {
  margin: 10px 0;
  width: 70%;
  display: flex;
  justify-content: space-between ;
}
.resultado{
  background-color: #c4c4c4;
}

</style>
