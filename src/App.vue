<script setup>
import { reactive, ref } from 'vue'
const usuario = reactive({
  nome: '',
  email : '' ,
  senha : '' ,
  confirmarsenha : '' ,
  datadenascimento : '',
  endereco : '',
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
const mostrarResultado = ref(false)
function validar() {
  let erro = false
  if (usuario.senha !== usuario.confirmarsenha) {
        alert("Senhas não batem")
        erro = true
    }
    if (!erro) {
        mostrarResultado.value = !mostrarResultado.value
    }
    }
</script>

<template>
  <div class="container">
    <div class="formulario">
      <h1>Formulario</h1>
      <form @submit.prevent="validar">
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
        <label for="">Endereço:</label>
        <input type="text" v-model="usuario.endereco" required >
      </div>
      <div class="row">
        <label for="">Cidade:</label>
        <input type="text" v-model="usuario.cidade" required >
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
        
        Linguagem:  <input type="radio" id="java" value="java" v-model="usuario.linguagens">
    <label for="java">Java</label>
    <input type="radio" id="js" value="js" v-model="usuario.linguagens">
    <label for="js">Java Script</label>
    <input type="radio" id="c" value="c" v-model="usuario.linguagens">
    <label for="c">C</label>
    <input type="radio" id="python" value="python" v-model="usuario.linguagens">
    <label for="python">Python</label>
      </div>
      <div clas="row">
        <label for =""> Hobbies </label>
        <input type="checkbox" id="jogos" value="jogos" v-model="usuario.hobby">
      <label for="jogos">Jogos</label>
      <input type="checkbox" id="artes" value="artes" v-model="usuario.hobby">
      <label for="artes">Artes</label>
      <input type="checkbox" id="musica" value="musica" v-model="usuario.hobby">
      <label for="musica">Música</label>
      </div>
      <div class="row">
        <label for = ""> Biografia: </label>
        <textarea v-model="usuario.biografia"></textarea>
            </div>
      <button type="submit">Mostrar</button>
    </form>
    </div>
    <div v-if="mostrarResultado" class="resultado">
      <h1>Resultado</h1>
      <p>Nome: {{ usuario.nome }}</p>
      <p>Email: {{ usuario.email }}</p>
      <p> Senha: {{ usuario.senha }}</p>
      <p> Data de Nascimento: {{ usuario.datadenascimento }}</p>
      <P> Endereço: {{ usuario.endereco }} </p>
      <P> Cidade: {{ usuario.cidade }} </p>
      <p> Estado: {{ usuario.estado }}</p>
      <p> Biografia: {{ usuario.biografia }}</p>
      <p> Linguagem: {{ usuario.linguagens }}</p>
      <p> Hobbies: {{ usuario.hobby }} </p>
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
