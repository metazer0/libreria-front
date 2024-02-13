<template>
        <h1>Listado de Libros</h1>
    <div :key="libro.id" v-for="libro in libros">
        <Libro @delete-libro="$emit('delete-libro', libro.id)" :libro="libro"/>
    </div>
</template>

<script>
import Libro from './Libro.vue';

    export default{
        name: 'Libros',
        components: {
            Libro
        },
        props:{
            libros: Array
        },
        emits: ['delete-libro']
    }
</script>