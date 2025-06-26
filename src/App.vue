<script setup>
import { ref, watch } from "vue";
import { Font } from "./model/font";

const inputUser = ref("");

// watch(inputUser, (nuevoValor) => {
//   if (nuevoValor !== "") {
//     document.documentElement.style.setProperty("--color-text", "#1c1c1e");
//   } else {
//     document.documentElement.style.setProperty("--color-text", "#888");
//   }
// });
// ============================
// MÉTODO 1) Usando una clase
// ============================

const korcy = new Font("Korcy", "'Korcy'");
const korcy_cursive = new Font("Korcy Cursive", "'Korcy Oblique', sans-serif");
const monospace = new Font("Monospace", "monospace");
const trebuchet = new Font(
  "Trebuchet MS",
  '"Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande","Lucida Sans", Arial, sans-serif'
);
const roboto = new Font(
  "Roboto",
  `system-ui, -apple-system, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif`
);

const fuentes = ref([korcy, monospace, trebuchet, roboto]);

</script>

<template>
  <main>
    <h1 :style="korcy_cursive">WeLoveFonts</h1>
    <input
      maxlength="64"
      type="text"
      id="inputUser"
      v-model="inputUser"
      placeholder="Introduce un texto"
    />
    <div class="box-content" v-for="(fuente, i) in fuentes" :key="i">
      <h3 :style="{ fontFamily: fuente.fontFamily }" class="fuente-uno">
        {{ fuente.name }}
      </h3>
      <p
        :style="{ fontFamily: fuente.fontFamily, fontWeight: 'bold' }"
        class="fuente-uno"
      >
        {{ inputUser !== "" ? inputUser : "We love fonts" }}
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
    display: block;
  }

  h3 {
    color: var(--color-text);
  }

  p {
    display: block;
    padding: 4px 4px;
    font-weight: bold;
    border: 0.1px dashed var(--color-text);
    word-break: break-word;
    white-space: normal;
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
