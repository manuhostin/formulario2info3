<script setup>
import { reactive, ref } from 'vue'

const mostrarResultado = ref(false) 
const usuario = reactive({
  nome: '',
  email : '' ,
  senha : '' ,
  confirmarsenha : '' ,
  datadenascimento : '',
  categorias : []
})
</script>

<template>
  <div class="container">
    <div class="formulario">
      <h1>Formulario</h1>
      <form @submit.prevent="mostrarResultado = !mostrarResultado">
      <div class="row">
        <label for="">Nome:</label>
        <input type="text" v-model="usuario.nome" required >
      </div>
      <div class="row">
        <label for="">Email:</label>
        <input type="email" v-model="usuario.email"/>
      </div>
      <div class="row">
        <label for="">Senha:</label>
        <input type="password" v-model="usuario.senha"/>
      </div>
      <div class="row">
        <label for="">Confirmar Senha:</label>
        <input type="password" v-model="usuario.confirmarsenha"/>
      </div>
      <button type="submit">Mostrar</button>
    </form>
    </div>
    <div class="row">
        <label for="">Data de Nascimento:</label>
        <input type="text" v-model="usuario.datadenascimento" required >
      </div>
    <div v-if="mostrarResultado" class="resultado">
      <h1>Resultado</h1>
      <p>Nome: {{ usuario.nome }}</p>
      <p>quantidade: {{ usuario.senha }}</p>
      <p>categorias: {{ usuario.categorias }}</p>
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
