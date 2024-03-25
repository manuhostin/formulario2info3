<script setup>
import { ref } from 'vue'

const titulo = ref('Título')

</script>

<template>
  <h1>{{ titulo }}</h1>
  <div class="container">
    <div class="formulario">
      <h1>Formulario</h1>
      <input type="text" v-model="titulo">
    </div>
    <div class="resultado">
      <h1>Resultado</h1>
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

.resultado{
  background-color: #c4c4c4;
}
</style>
