<script setup>
import { ref } from "vue";

const inputUser = ref("");
const fuentes = ref([
  "'Korcy'",
  'monospace',
  '"Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande","Lucida Sans", Arial, sans-serif',
  `'system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif'`,
]);
const fuenteName=ref(["Korcy","Monospace","Trebuchet MS","Roboto" ])
</script>

<template>
  <main>
    <h1>WeLoveFonts</h1>
    <input
      type="text"
      id="inputUser"
      v-model="inputUser"
      placeholder="Introduce un texto"
    />
    <div class="box-content" v-for="(fuente, i) in fuentes" :key="i">
      <h3 :style="{ fontFamily: fuente }" class="fuente-uno">{{fuenteName[i]}}</h3>
      <p :style="{ fontFamily: fuente, fontWeight: 'bold' }" class="fuente-uno">
        {{ inputUser }}
      </p>
      <button id="botonUno">Copiar</button>
    </div>
  </main>
</template>

<style scoped></style>
