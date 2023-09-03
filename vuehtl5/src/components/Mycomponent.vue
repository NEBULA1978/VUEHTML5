<template>
    <div class="my-component">
        <!-- directiva v-if abreviado : -->
        <h1 v-if="isVisible">{{ message }}</h1>
        <!-- cambiamos el texto de color al pulsar el boton -->
        <h2 v-bind:class="{ isHighlighted: isHighlighted}">{{ title }}</h2>
        <!-- modificamos el valor de isVisible con el boton -->
        <!-- <button v-on:click="isVisible = !isVisible">Toggle visibility</button> -->
        <!-- llamamoscon metodo con nombre de funcion de abajo -->
        <!-- <button @click="toggleVisibility">Toggle visibility</button> -->
        <button v-on:click="toggleVisibility">Toggle visibility</button>
        <button v-on:click="sayHello">Toggle visibility</button>
        <button v-on:click="toggleHighted">Toggle Highlight</button>
        <!-- v-model comunicacion dual -->
        <input v-model="message">
        
        <!-- v-for -->
        <ul>
            <!-- por cada uno de los items que este en la lista imprime -->
            <li v-for="item in list" :key="item.id">{{ item.text }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'my-component',
    data() {
        return {
            message: 'Hello world with Vue 3',
            title:'This is the title',
            isHighlighted:true,
            isVisible: true,
            list:[
                {id:1, text:'First item'},
                {id:2, text:'Second item'},
                {id:3, text:'Third item'},
            ]
        }
    },
    // creamos funcion para modificar valor de variable isVisible
    methods:{
        toggleVisibility(){
            this.isVisible = !this.isVisible
        },
        sayHello(){
            alert('hello')
        },
        // para cambiar el color con el estado
        toggleHighted(){
            this.isHighlighted = !this.isHighlighted;
        }
    }

}
</script>

<style>
.isHighlighted{
    color:gold;
}
</style>