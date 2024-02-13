<template>
    <h3>{{libro.nombreLibro}}</h3>
    <p>{{ libro. autores }}</p>
</template>

<script>
    export default{
        name: 'Libro',
        props:{
            libro: Object
        }
    }
</script>