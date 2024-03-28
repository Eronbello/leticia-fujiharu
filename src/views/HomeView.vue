<script setup>
import imageOne from "../assets/imagem1.jpeg";
import imagem2 from "../assets/imagem2.jpeg";
import imagem3 from "../assets/imagem3.jpeg";
import imagem4 from "../assets/imagem4.jpeg";
import imagem5 from "../assets/imagem5.jpeg";
import trumpetSfx from "../assets/music.mp3";
import Letters from '../components/Letters.vue';

const audio = new Audio(trumpetSfx);

import { onMounted, ref, watch } from 'vue';

const showModal = ref(false);
const images = ref([
imageOne,
imagem2,
imagem3,
imagem4,
imagem5,
]);
const currentImageIndex = ref(0);
const currentImage = ref(images.value[currentImageIndex.value]);
const title = ref('Leticia Narumi Fujiharu');
const message = ref('Você é a razão do meu sorriso. Te amo mais que tudo!');

const updateBackgroundImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.value.length;
  currentImage.value = images.value[currentImageIndex.value];
};

const handleClick = () => {
  showModal.value = true
  audio.play()
}

onMounted(() => {
  const intervalId = setInterval(updateBackgroundImage, 500); // Atualiza a imagem a cada 3 segundos
  watch(showModal, (newVal) => {
    if (!newVal) {
      clearInterval(intervalId);
    }
  });
});
</script>

<template>
  <main>
    <h1 @click="handleClick">Alfabeto de receitas</h1>
    <Letters />
    <div v-if="showModal" class="modal" :style="{ backgroundImage: 'url(' + currentImage + ')' }">
      <div class="content">
        <h1>{{ title }}</h1>
        <p>{{ message }}</p>
        <p>Nosso namoro está dando os primeiros passos, mas sinto que nosso amor já vem de outras vidas. E sete meses depois só peço que seja para sempre, que este sentimento seja infinito. Pois quero poder me sentir assim a vida toda, feliz, como se por fim tudo estivesse no lugar.

É verdade que 7 meses é pouco, é um tempo pequenininho, mas para mim bastou para saber que quero viver mil vidas ao seu lado. Te amo!</p>
        <button @click="showModal = false">Fechar</button>
      </div>
    </div>
  </main>
</template>


<style scoped>
h1 {
  margin-bottom: 3rem;
  margin-top: 1rem;
  text-align: center;
  font-size: 2rem;
}

main {
  height: 100vh;
  width: 100vw;
  background-image: url("https://static.vecteezy.com/system/resources/previews/016/651/877/non_2x/happy-cute-couple-free-png.png");
  background-position: center;
  background-size: cover;
  padding: 1rem;
}

.modal {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-size: cover;
  background-position: center;
  color: white;
}

.content {
  text-align: center;
  width: 100%;
  height: 100%;
  padding: 20px;
  background-color: rgba(0, 0, 0, 0.5); /* Fundo semi-transparente */
}

button {
  margin-top: 20px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
</style>