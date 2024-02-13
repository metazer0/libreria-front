<template>
  <div class="container justify-content-center">
    <Libros :libros="libros"/>
  </div>
</template>


<script>
import Libros from '@/components/Libros.vue';

  export default{
    name: 'Home',
    components: {
      Libros
    },
    methods:{
      async fetchLibros(){
        const res = await fetch('https://localhost:7019/Libreria')
        return await res.json();
      }
    },
    data(){
      return{
        libros: []
      }
    },
    async created(){
      this.libros = await this.fetchLibros()
    }
  }
</script>