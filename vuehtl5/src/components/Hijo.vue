<template>
    <div>
        <h1>HiIJO</h1>
        <h2>Te llamas {{ nombre }} y tienes {{ edad }} años</h2>
        <button @click="enviar">Cambiar valores del padre desde el hijo</button>
        <!-- Display previous values if the button has been clicked -->
        <div v-if="buttonClicked">
            <p>Valores actuales:Te llamas {{ nombre }} y tienes {{ edad }} años</p>
            <p>Nombre anterior: {{ previousNombre }}</p>
            <p>Edad anterior: {{ previousEdad }}</p>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";

const { nombre, edad, previousNombre, previousEdad } = defineProps([
    "nombre",
    "edad",
    "previousNombre",
    "previousEdad",
]);

const buttonClicked = ref(false);

const emit = defineEmits(["modificar"]);

const enviar = () => {
    emit("modificar", "Vue", 9);
    buttonClicked.value = true; // Set the buttonClicked to true when clicked
};
</script>

<style></style>
