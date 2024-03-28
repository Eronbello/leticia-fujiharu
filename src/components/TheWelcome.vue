<template>
  <div class="alfabeto-container">
    <div class="card" v-for="letra in alfabeto" :key="letra">
      {{ letra }}
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const alfabeto = ref('ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split(''));
</script>

<style>
.alfabeto-container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px; /* Espaço entre os cards */
  justify-content: center; /* Centraliza os cards na linha */
}

.card {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px; /* Largura do card */
  height: 50px; /* Altura do card */
  background-color: #f3f3f3; /* Cor de fundo do card */
  border: 1px solid #ddd; /* Borda do card */
  border-radius: 8px; /* Arredondamento da borda */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2); /* Sombra para dar aspecto de elevação */
  font-weight: bold; /* Torna a letra em negrito */
  font-size: 1.2em; /* Tamanho da fonte */
}

.card:hover {
  cursor: pointer;
}
</style>
