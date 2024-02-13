<template>
    <div :key="libro.id" v-for="libro in libros">
        <Libro :libro="libro"/>
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
        }
    }
</script>