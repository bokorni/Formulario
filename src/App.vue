<script setup>
import { reactive, ref } from 'vue';

const titulo = ref('Oi Vuejs');
const mostrarResult = ref(false);
const produto = reactive(
  {
    nome: '',
    preco: 0,
    quantidade: 0,
    categoria:[]
  }
)
</script>

<template>
  <h2>{{ titulo }}</h2>
  <div class="container">
    <div class="formulario">
      <h2>formulario</h2>
      <input type="text" v-model="titulo">
    </div>
    <div class="row">
      <label for="">Nome:</label>
      <input type="text">
    </div>
    <div class="row">
      <label for="">Preço:</label>
      <input type="text">
    </div>
    <div class="row">
      <label for=""></label>
      <input type="text">
    </div>
    <div v-if="mostrarResult" class="result">
      <h2>Dados do produto</h2>
      <p>Nome:{{ produto.nome }}</p>
      <p>Preço:{{ produto.preco }}</p>
      <p>Em estoque:{{ produto.quantidade }} </p>
      <p>Comprados: {{ produto.categoria }}</p>
    </div>
  </div>
  <div>
    <div>
      <h1>Oi</h1>
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
}

.formulario {
  background-color: rgb(224, 63, 57);

}

.formulario 
.row {
  margin: 1.3rem 0;
  display: flex;
  width: 80%;
  justify-content: space-between;
}

.result {
  background-color: rgb(114, 211, 114);
}
</style>
