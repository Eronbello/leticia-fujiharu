<template>
  <div class="receita">
    <h1>{{ titulo }}</h1>
    <p class="descricao">{{ descricao }}</p>
    <div class="galeria-imagens">
      <img
        v-for="(imagem, index) in imagens"
        :src="imagem"
        :alt="`Imagem ${index + 1} da receita`"
        :key="index"
        class="imagem-receita"
      />
    </div>
    <div class="modo-preparo">
      <h2>Modo de Preparo</h2>
      <ol>
        <li v-for="(passo, index) in modoPreparo" :key="index">
          {{ passo }}
        </li>
      </ol>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

// Definindo props para passar os dados da receita
const props = defineProps({
  titulo: String,
  descricao: String,
  imagens: Array,
  modoPreparo: Array
});
</script>

<style>
.receita {
  max-width: 600px;
  margin: auto;
  padding: 20px;
}

.receita h1 {
  margin-bottom: 10px;
}

.descricao {
  margin-bottom: 20px;
}

.galeria-imagens {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
  overflow-x: auto;
}

.imagem-receita {
  border-radius: 8px;
  max-height: 200px;
  object-fit: cover;
}

.modo-preparo h2 {
  margin-bottom: 10px;
}

.modo-preparo ol {
  list-style-position: inside;
  padding: 0;
}
</style>
