<!-- Vista Principal -->

<template>
  <div class="container justify-content-center">
    <!-- modulo para agregar libro -->
    <AddLibro @new-libro="newLibro"/>
    <!-- modulo para visualizar y eliminar libro -->
    <Libros @delete-libro="deleteLibro" :libros="libros"/>
  </div>
</template>


<script>
import Libros from '@/components/Libros.vue';
import AddLibro from '@/components/AddLibro.vue';

  export default{
    name: 'Home',
    components: {
      Libros,
      AddLibro
    },
    methods:{
      async fetchLibros(){
        const res = await fetch('https://localhost:7019/Libreria')
        return await res.json();
      },
      async deleteLibro(id){
        try {
          const res = await fetch(`https://localhost:7019/Libreria/${id}`,{
            method: 'DELETE'
          })
          if(res.status === 204){
            this.libros = this.libros.filter( l => l.id !== id)
            alert('libro eliminado exitosamente')
          }else{
            alert('error al eliminar libro')
          }
        } catch (error) {
          alert(error)
        }
      },
      async newLibro(libro){
        let newLibro = libro

        const res = await fetch('https://localhost:7019/Libreria',{
          method:'POST',
          headers:{
            'content-type': 'application/json'
          },
          body: JSON.stringify(newLibro)
        })

  
        this.libros = [...this.libros, newLibro]
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