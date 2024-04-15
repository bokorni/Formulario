<script setup>
import { reactive, ref } from 'vue';


const mostrarResult = ref(false);
const linguagens = ['', '', '', ''];
const infos = reactive({
  nome: '',
  email: '',
  senha: '',
  confirma: '',
  data: '',
  endereco: '',
  cidade: '',
  hobbies: '',
  biografia: ''
})
const estado = ref([
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
]);
</script>

<template>
  <h2>{{ titulo }}</h2>
  <div class="container">
    <div class="formulario">
      <h2>Cadastre-se</h2>
      <input type="text" v-model="titulo">
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
          <option value="estado.uf" v-for="(estado) in estados" :key="estado.uf">{{ estado.name }}</option>
        </select>
      </div>
          


      <fieldset>
        <Legend>linguagens</Legend>
        <div class="items-checkbox">

          <template v-for="linguagem in linguagens" :key="linguagem">
            <input type="checkbox" :value="linguagem" v-model="infos.linguagens" /> {{ linguagem }}
          </template>
        </div>
      </fieldset>
      <button @click="mostrarResult = !mostrarResult">Mostrar</button>
    </div>
    <div class="result">

      <div v-if="mostrarResult" class="result">
        <h2>Informações</h2>
        <p>Nome:{{ infos.nome }}</p>
        <p>Preço:{{ infos.preco }}</p>
        <p>Em estoque:{{ infos.quantidade }} </p>
        <p>Categoria: {{ infos.categorias }}</p>
        <p v-for="linguagem in infos.linguagens" :key="linguagem"></p>
        <p>{{ mostrarResult }}</p>
      </div>

    </div>
  </div>


</template>

<style scoped>
.container {
  display: flex;
  gap: 2rem;
  justify-content: center;
  margin-top: 1rem;
}

.formulario,
.result {
  width: 45vw;
  min-height: 70vh;
  border-radius: 20px;
  padding: 20px;
}

.formulario {
  background-color: rgb(224, 63, 57);

}

.formulario .row {
  margin: 1.3rem 0;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 80%;
}

.result {
  background-color: rgb(114, 211, 114);
}
</style>
