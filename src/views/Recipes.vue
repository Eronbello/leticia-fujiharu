<script setup>
import { ref } from 'vue';
import { useRoute, useRouter } from 'vue-router';
import RecipesJson from '../assets/recipes.json';
import Recipe from '../components/Recipe.vue';

const route = useRoute();  
const router = useRouter();
const id = route.params.letter; // read parameter id (it is reactive) 
const recipesjson = ref(RecipesJson);
</script>

<template>
  <main>
    <span @click="router.push('/')">Voltar</span>
    <h1>Letra: {{ id }}</h1>
    <Recipe :titulo="recipesjson[id].titulo" :descricao="recipesjson[id].descricao" :modo-preparo="recipesjson[id].modoPreparo" :imagens="recipesjson[id].imagens"/>
  </main>
</template>


<style scoped>
h1 {
  margin-top: 1rem;
  text-align: center;
  font-size: 2rem;
}

main {
  height: 100vh;
  width: 100vw;
  /* background-image: url("https://static.vecteezy.com/system/resources/previews/016/651/877/non_2x/happy-cute-couple-free-png.png");
  background-position: center;
  background-size: cover; */
  padding: 1rem;
}
</style>