<script setup>
import { reactive, ref } from 'vue'

const mostrarResultado = ref(false) 
const usuario = reactive({
  nome: '',
  email : '' ,
  senha : '' ,
  confirmarsenha : '' ,
  datadenascimento : '',
  cidade : '',
  estado : '',
  hobby : [],
  linguagens : '',
  biografia : '' 
})
const estados = [
  { uf: 'AC', name: 'Acre' },
  { uf: 'AL', name: 'Alagoas' },
  { uf: 'AP', name: 'Amapá' },
  { uf: 'AM', name: 'Amazonas' },
  { uf: 'BA', name: 'Bahia' },
  { uf: 'CE', name: 'Ceará' },
  { uf: 'DF', name: 'Distrito Federal' },
  { uf: 'ES', name: 'Espírito Santo' },
  { uf: 'GO', name: 'Goiás' },
  { uf: 'MA', name: 'Maranhão' },
  { uf: 'MT', name: 'Mato Grosso' },
  { uf: 'MS', name: 'Mato Grosso do Sul' },
  { uf: 'MG', name: 'Minas Gerais' },
  { uf: 'PA', name: 'Pará' },
  { uf: 'PB', name: 'Paraíba' },
  { uf: 'PR', name: 'Paraná' },
  { uf: 'PE', name: 'Pernambuco' },
  { uf: 'PI', name: 'Piauí' },
  { uf: 'RJ', name: 'Rio de Janeiro' },
  { uf: 'RN', name: 'Rio Grande do Norte' },
  { uf: 'RS', name: 'Rio Grande do Sul' },
  { uf: 'RO', name: 'Rondônia' },
  { uf: 'RR', name: 'Roraima' },
  { uf: 'SC', name: 'Santa Catarina' },
  { uf: 'SP', name: 'São Paulo' },
  { uf: 'SE', name: 'Sergipe' },
  { uf: 'TO', name: 'Tocantins' }
]
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
      <div class="row">
        <label for="">Data de Nascimento:</label>
        <input type="date" v-model="usuario.datadenascimento" required >
      </div>
      <div class="row">
        <label for="">Estado:</label>
        <select v-model = "usuario.estado" required>
              <option selected disabled value="">Selecionar...</option>
              <option v-for="estado of estados" :key="estado.uf" :value="estado.uf">
                {{ estado.name }}
              </option>
            </select>
      </div>
      <div class="row">
        <label for = ""> Biografia: </label>
        <textarea v-model="usuario.biografia"></textarea>
        {{ biografia.name }}
      </div>
      <div class="row">
        <label for = ""> Hobbies: </label>
        <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
        <label for="jack">Jack</label>
        <input type="checkbox" id="john" value="John" v-model="checkedNames">
        <label for="john">John</label>
        <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
        <label for="mike">Mike</label>
      </div>
      <button type="submit">Mostrar</button>
    </form>
    </div>
    <div v-if="mostrarResultado" class="resultado">
      <h1>Resultado</h1>
      <p>Nome: {{ usuario.nome }}</p>
      <p>Email: {{ usuario.email }}</p>
      <p> Senha: {{ usuario.senha }}</p>
      <p> Estado: {{ usuario.estado }}</p>
      <p> Estado: {{ usuario.biografia }}</p>

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
