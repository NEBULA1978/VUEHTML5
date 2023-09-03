<template>
  <div>
    <header>
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    </header>
    <div>
      <h1>PADRE:</h1>
      <!-- El padre le envía al hijo estos dos valores, el hijo recibe -->
      <!-- Cuando el hijo utilice: cambiarValor, recibe valores, el hijo le envía -->
      <HijoVue :nombre="nombre" :edad="edad" :previousNombre="previousNombre" :previousEdad="previousEdad"
        @modificar="cambiarValor" />
      <HijoVue2 />
      <Mycomponent />
      <button @click="abrirIndexHTML">Abrir index.html en nueva ventana</button>
    </div>
  </div>
</template>

<script setup>
import { ref, provide } from "vue";
import HijoVue from "./components/Hijo.vue";
import HijoVue2 from "./components/Hijo2.vue";

// Valores del padre
const nombre = ref("JAB");
const edad = ref(18);
let previousNombre = nombre.value;
let previousEdad = edad.value;

// hijo2 modificamos este texto de App.vue
// no enviamos como props pero el hijo tiene que recibir
const canal = ref("soyjab");
// me permite darle un nombre a este valor y desde el hijo hacer referencia a este valor
// cuando quiera recibir canal lo haré a través de miCanal (provide: enviar no recibe)
provide('miCanal', canal);

// Función para cambiar valores Vue 3 y 9
const cambiarValor = (valor1, valor2) => {
  previousNombre = nombre.value;
  previousEdad = edad.value;
  nombre.value = valor1;
  edad.value = valor2;
};

// Función para abrir index.html en una nueva ventana
const abrirIndexHTML = () => {
  const rutaIndexHTML = "./src/curso-HTMl-Empinnos-master/index.html"; // Ajusta la ruta según tu estructura de directorios
  window.open(rutaIndexHTML, '_blank');
};
</script>

<style scoped>
.logo {
  display: block;
  margin: 0 auto 2rem;
}
</style>
