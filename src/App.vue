<script setup>
import { ref } from "vue";

const inputUser = ref("");

const korcy_oblique = {
  name: "Korcy",
  fontFamily: "'Korcy Oblique'",
};

const korcy = {
  name: "Korcy",
  fontFamily: "'Korcy'",
};
const monospace = {
  name: "Monospace",
  fontFamily: "monospace",
};
const trebuchet = {
  name: "Trebuchet MS",
  fontFamily:
    '"Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande","Lucida Sans", Arial, sans-serif',
};
const roboto = {
  name: "Roboto",
  fontFamily: '"Roboto", sans-serif',
};
const fuentes = ref([korcy, monospace, trebuchet, roboto]);
</script>

<template>
  <!-- Fuente Roboto -->
  <link
    href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap"
    rel="stylesheet"
  />

  <main>
    <h1 :style="korcy_oblique">WeLoveFonts</h1>
    <input
      maxlength="64"
      type="text"
      id="inputUser"
      v-model="inputUser"
      placeholder="Introduce un texto"
    />
    <div class="box-content" v-for="fuente in fuentes">
      <h3 :style="{ fontFamily: fuente.fontFamily }" class="fuente-uno">
        {{ fuente.name }}
      </h3>
      <p
        :style="{ fontFamily: fuente.fontFamily, fontWeight: 'bold' }"
        class="fuente-uno"
      >
        {{ inputUser }}
      </p>
      <button id="botonUno">Copiar</button>
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  width: 100%;
  text-align: center;
  align-items: center;
  align-content: center;
  justify-content: center;
  h1 {
    font-family: "Korcy", sans-serif;
    font-size: 3rem;
    margin-top: 100px;
    gap: 30px;
  }
  input {
    margin-top: 20px;
    width: 300px;
    height: 20px;
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
  border: 2px solid var(--color-background-card);
  background-color: var(--color-background-card);
  border-radius: 12px;
  width: 300px;
  gap: 16px;
  display: flex;
  flex-direction: column;
  text-align: left;
  margin: 20px;
  padding: 10px;

  .fuente-uno {
    word-wrap: break-word;
    overflow-wrap: break-word;
    white-space: normal;
    display: block;
    width: 100%;
    max-width: 100%;
    height: auto;
    line-height: 1.4;
    justify-content: center;
  }

  h3 {
    color: var(--color-text);
  }

  p {
    padding: 2px;
    display: flex;
    align-items: center;
    min-height: 30px;
    border: 0.1px dashed var(--color-text);
  }

  button {
    color: var(--color-text);
    background-color: var(--color-background-button);
    padding: 8px;
    width: 80px;
    border: none;
    border-radius: 5px;
    &:hover {
      background-color: #eae9e9;

      transition: background-color 0.1s ease;
    }
  }
}
</style>
