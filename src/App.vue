<script setup>
import { reactive, ref } from 'vue';
const linguagens = ref('');

const mostrarResult = ref(true)
function addlang() {
  if (linguagens.value == '' || !infos.email.includes('@') || infos.confirma != infos.senha) {
    alert('Preencha todos campo CORRETAMENTE')
  }
  else {
    infos.linguagens.push(linguagens.value)
    linguagens.value = ''
    mostrarResult.value = !mostrarResult.value
  }

}
const infos = reactive({
  nome: '',
  email: '',
  senha: '',
  confirma: '',
  data: '',
  endereco: '',
  cidade: '',
  hobbies: '',
  biografia: '',
  linguagens: []
})


const estado = ref('');
const states = reactive([
  { uf: 'AC -', name: 'Acre' },
  { uf: 'AL -', name: 'Alagoas' },
  { uf: 'AP -', name: 'Amapá' },
  { uf: 'AM -', name: 'Amazonas' },
  { uf: 'BA -', name: 'Bahia' },
  { uf: 'CE -', name: 'Ceará' },
  { uf: 'DF -', name: 'Distrito Federal' },
  { uf: 'ES -', name: 'Espírito Santo' },
  { uf: 'GO -', name: 'Goiás' },
  { uf: 'MA -', name: 'Maranhão' },
  { uf: 'MT -', name: 'Mato Grosso' },
  { uf: 'MS -', name: 'Mato Grosso do Sul' },
  { uf: 'MG -', name: 'Minas Gerais' },
  { uf: 'PA -', name: 'Pará' },
  { uf: 'PB -', name: 'Paraíba' },
  { uf: 'PR -', name: 'Paraná' },
  { uf: 'PE -', name: 'Pernambuco' },
  { uf: 'PI -', name: 'Piauí' },
  { uf: 'RJ -', name: 'Rio de Janeiro' },
  { uf: 'RN -', name: 'Rio Grande do Norte' },
  { uf: 'RS -', name: 'Rio Grande do Sul' },
  { uf: 'RO -', name: 'Rondônia' },
  { uf: 'RR -', name: 'Roraima' },
  { uf: 'SC -', name: 'Santa Catarina' },
  { uf: 'SP -', name: 'São Paulo' },
  { uf: 'SE -', name: 'Sergipe' },
  { uf: 'TO -', name: 'Tocantins' }
]);
</script>

<template>
  <h2>{{ titulo }}</h2>
  <div class="container" v-if="mostrarResult">
    <div class="formulario">
      <h2>Cadastre-se</h2>


      <div class="row">
        <label for="">Nome:</label>
        <input type="text" v-model="infos.nome">
      </div>

      <div class="row">
        <label for="">E-mail:</label>
        <input type="text" v-model="infos.email">
      </div>

      <div class="row">
        <label for="">Senha:</label>
        <input type="password" v-model="infos.senha">
      </div>

      <div class="row">
        <label for="">Confirmação de senha:</label>
        <input type="password" v-model="infos.confirma">
      
      </div>
      <div class="row">
        <label for="">Data de nascimento:</label>
        <input type="date" v-model="infos.data">
      </div>
      <div class="row">
        <label for="">Endereço:</label>
        <input type="text" v-model="infos.endereco">
      </div>
      <div class="row">
        <label for="">Cidade:</label>
        <input type="text" v-model="infos.cidade">
      </div>
      <div class="row">
        <label for="text">Estado:</label>
        <select name="estados" id="estados" v-model="estado">
          <option value="state.uf" v-for="state in states" :key="state.uf"> {{ state.uf }} {{ state.name }} </option>
        </select>
      </div>
      <div class="row">
        <label for="">Hobbies:</label>
        <input type="text" v-model="infos.hobbies">
      </div>
      <div class="row">
        <label for="">Biografia:</label>
        <input type="text" v-model="infos.biografia">
      </div>
      <div class="row">
        <label for="">Diga quais são suas linguagens preferidas:</label>
        <input type="text" v-model="linguagens">
        
        <div class="botao">
          <button @click="addlang">Enviar</button>

        </div>
      </div>

    </div>
    <div class="result">

      <p>@bokorn1</p>

    </div>
  </div>

  <div v-else class="result">
    <h2>Informações</h2>
    <p>Nome:{{ infos.nome }}</p>
    <p>E-mail:{{ infos.email }}</p>
    <p>Senha:{{ infos.senha }} </p>
    <p>Data de nascimento: {{ infos.data }}</p>
    <p>Endereço: {{ infos.endereco }}</p>
    <p>Cidade: {{ infos.cidade }}</p>
    <p>Hobbies: {{ infos.hobbies }}</p>
    <p>Biografia:{{ infos.biografia }}</p>
    <div class="language">
      <p>Linguagens:</p>
      <p v-for="langs in infos.linguagens" :key="langs"> {{ langs  }}</p>
    </div>

    <button @click="mostrarResult = true">Voltar</button>
  </div>

</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Amarante&display=swap');

* {
  font-family: "Amarante", serif;
}
.botao
  {
   
  display: flex;
  justify-content: center;
  padding: 3vw;
  
  border: none;
  color: rgb(20, 250, 70);
 
}
.container {
  width: 50vw;
  padding: 40px;
  border-radius: 20px;
}

h2 {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}



label {
  color: rgb(20, 250, 70)
}

.container,
.formulario {
  width: 60vw;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 25px;
}

.container .formulario h2 {
  color: rgb(20, 250, 70);
  font-weight: 500;
  letter-spacing: 0.1rem;
}

.container,
.formulario,
.row {
  position: relative;
  width: 100vw;

}

.formulario .row {
  margin: 1.3rem 0;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 80%;
}


.result {
  width: 50vw;
  padding: 40px;
  border-radius: 20px;
  border: 8px solid #223243;
  box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35),
    inset -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35),
    inset -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
  width: 60vw;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 25px;
  color: #FFF
}



 
.formulario {
  padding: 12px 10px 12px 48px;
  border: none;
  width: 60vw;
  background: #223243;
  border: 1px solid rgba(0, 0, 0, 0.1);
  color: #FFF;
  font-weight: 300;
  border-radius: 25px;
  font-size: 1em;
  box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
  transition: 0.5s;
  outline: none;

}

input,
select {
  background: #223243;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 25px;
  box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
  padding: 12px 10px 12px 48px;
  border: none;
  color: rgb(255, 255, 255);
}

;


.check {
  width: 2vw;
}

.items-checkbox {
  display: flex;
  flex-direction: column;
}

button {
  background: #223243;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 25px;
  box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
  padding: 12px 10px 12px 10px;
  border: none;
  color: rgb(20, 250, 70);
}
</style>
