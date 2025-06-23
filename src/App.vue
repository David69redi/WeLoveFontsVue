<script setup>
import { ref } from "vue";
import ComponentInput from "./components/ComponentInput.vue";
const inputUser = ref("");
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
    <!-- <ComponentInput /> -->
    <div class="box-content">
      <h3 class="fuente-uno">Korcy</h3>
      <p class="fuente-uno">{{ inputUser }}</p>
      <button id="botonUno">Copiar</button>
    </div>
  </main>
</template>

<style scoped>
@font-face {
  font-family: "YoungMorin";
  src: url("./fonts/YoungMorin-Regular.ttf") format("truetype");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "Korcy";
  src: url("./fonts/Korcy.ttf") format("truetype");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "Korcy Oblique";
  src: url("./fonts/Korcy Oblique.ttf") format("truetype");
  font-weight: normal;
  font-style: normal;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

main {
  display: flex;
  flex-direction: column;
  width: 100%;
  text-align: center;
  align-items: center;
  align-content: center;
  justify-content: center;
  h1 {
    font-family: "Korcy Oblique", sans-serif;
    font-size: 3rem;
    margin-top: 100px;
    gap: 30px;
  }
  input {
    width: 300px;
    height: 40px;
    border: none;
    border-bottom: 1px solid transparent;
    outline: none;
    transition: border-bottom-color 0.3s ease;

    &:focus {
      border-bottom: 1px solid black;
    }
  }
}

.box-content {
  width: 300px;
  gap: 8px;
  display: flex;
  flex-direction: column;
  text-align: left;

  p {
    display: flex;
    align-items: center;
    min-height: 30px;
    border: 0.1px dashed black;
  }

  button {
    padding: 10px;
    width: 80px;
    border: none;
    border-radius: 5px;
  }
}
</style>
