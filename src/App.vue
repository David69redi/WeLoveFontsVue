<script setup>
import { ref } from "vue";
import BotonCopiar from "./assets/components/BotonCopiar.vue";
import SwitchTema from "./assets/components/SwitchTema.vue";

async function copiarTexto(key) {
  try {
    await navigator.clipboard.writeText(inputUser.value);
    console.log(key);
  } catch (error) {
    alert("No tengo permiso para copiar el texto");
  }
}

const inputUser = ref("");

const darkTheme = ref("");

const korcy_oblique = {
  name: "Korcy",
  fontFamily: "'Korcy Oblique'",
};

const fuentes = ref([
  {
    name: "Korcy",
    fontFamily: "'Korcy'",
  },
  {
    name: "Monospace",
    fontFamily: "monospace",
  },
  {
    name: "Trebuchet MS",
    fontFamily:
      '"Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande", "Lucida Sans", Arial, sans-serif',
  },
  {
    name: "Roboto",
    fontFamily: '"Roboto", sans-serif',
  },
]);
</script>

<template>
  <!-- Fuente Roboto -->
  <link
    href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap"
    rel="stylesheet"
  />

  <main :class="darkTheme">
    <!-- <img src="./assets/svg/LogoWLF.svg" alt="Logo" class="logo" /> -->
    <aside>
      <SwitchTema
        @click="
          () => {
            darkTheme = darkTheme === 'dark-theme' ? '' : 'dark-theme';
          }
        "
      />
    </aside>

    <h1 :style="korcy_oblique">WeLoveFonts</h1>
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
        {{ inputUser }}
      </p>

      <BotonCopiar @click="copiarTexto(i)" />
    </div>
  </main>
</template>

<style scoped>
main {


  



  color: var(--color-text);
  background-color: var(--color-background-body);
  display: flex;
  flex-direction: column;
  width: 100%;
  text-align: center;
  align-items: center;
  align-content: center;
  justify-content: center;
 
  background-image: radial-gradient(var(--second-color-background-body) 0.5px, transparent 0.5px);
  background-size: 20px 20px;

  /* .logo {
    margin-top: 4rem;
    width: 500px;
    height: auto;
  } 
*/

  aside {
    margin-top: 3rem;
    width: 100%;
    /* border: 1px solid blue; */
    display: flex;
    align-items: center;
    justify-content: flex-end;
    font-size: 1rem;
  }
  h1 {
    font-family: "Korcy", sans-serif;
    font-size: 3rem;
    margin-top: 20px;
    gap: 30px;
  }
  input {
    color: var(--color-text);
    margin-top: 20px;
    width: 300px;
    height: 20px;
    border: none;
    border-bottom: 1px solid transparent;
    outline: none;
    transition: border-bottom-color 0.3s ease;
    background: none;

    &:focus {
      border-bottom: 1px solid var(--color-text);
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
}
</style>
