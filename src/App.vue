<script setup lang="ts">
import { ref } from "vue";
const desabafo = ref("");
const mostrarResposta = ref(false);
const loading = ref(false);
const enviarDesabafo = () => {
  loading.value = true;
  setTimeout(() => {
    mostrarResposta.value = true;
    loading.value = false;
  }, 1500);
};
</script>

<template>
  <div>
    <h2>Conte seus problemas</h2>
    <div class="form">
      <textarea ref="desabafo" @keydown.enter="enviarDesabafo" />
      <button @click="enviarDesabafo">enviar</button>
    </div>
    <img
      v-if="loading"
      src="./assets/loading-load.gif"
      alt="loading gif"
      width="40px"
    />
    <h3 v-if="mostrarResposta">É foda</h3>
  </div>
</template>

<style lang="scss" scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: center;
  margin-bottom: 1rem;

  button {
    width: 50%;
  }
}
</style>
