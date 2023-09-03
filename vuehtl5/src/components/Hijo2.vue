<template>
    <div>
        <h1>HiIJO2</h1>
        <h2>{{ canal }}</h2>
        <!-- boton para cambiar el valor del teto de la variable de este hijo2 -->
        <button @click="modificar">cambiar texto variable Hijo2</button>
    </div>
</template>

<script setup>
import { inject } from 'vue';

// desde provide comunicamos miCanal con los valores de este canal inject recibimos no enviamos
const canal=inject('miCanal')

const modificar=()=>{
    canal.value="html6"
} 
</script>

<style></style>
