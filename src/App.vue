<script setup>
import { reactive, ref } from 'vue';

const titulo = ref('Oi Vuejs');
const mostrarResult = ref(false);
const categorias = ['Eletronicos', 'Moveis', 'Vestuario', 'Brinquedo'];
const produto = reactive({
  nome: '',
  preco: 0,
  quantidade: 0,
  categorias: []

})
</script>

<template>
  <h2>{{ titulo }}</h2>
  <div class="container">
    <div class="formulario">
      <h2>formulario</h2>
      <input type="text" v-model="titulo">
      <div class="row">
        <label for="">Nome:</label>
        <input type="text" v-model="produto.nome">
      </div>

      <div class="row">
        <label for="">Preço:</label>
        <input type="text" v-model="produto.preco">
      </div>

      <div class="row">
        <label for="">Quantidade:</label>
        <input type="text" v-model="produto.quantidade">
      </div>

      <div class="row">
        <label for="">Categoria:</label>
        <input type="text" v-model="produto.categoria">
      </div> 

      <fieldset>
        <Legend>categorias</Legend>
        <div class="items-checkbox">
          
          <template v-for="categoria in categorias" :key="categoria">
            <input type="checkbox" :value="categoria" v-model="produto.categorias" /> {{ categoria }}
          </template>
        </div>
      </fieldset>
      <button @click="mostrarResult = !mostrarResult">Mostrar</button>
      </div>
      <div class="result">

        <div v-if="mostrarResult" class="result">
          <h2>Dados do produto</h2>
          <p>Nome:{{ produto.nome }}</p>
          <p>Preço:{{ produto.preco }}</p>
          <p>Em estoque:{{ produto.quantidade }} </p>
          <p>Categoria: {{ produto.categorias }}</p>
          <p v-for="categoria in produto.categorias" :key="categoria"></p>
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
