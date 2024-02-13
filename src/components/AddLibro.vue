<template>
    <form @submit="onSubmit" class="add-form">
      <div class="formm-control">
        <label>Nombre Libro</label>
        <input type="text" name="text" v-model="nombre" placeholder="Agregar Libro">
      </div>
      <div class="formm-control">
        <label for="">Autor</label>
        <input type="text" name="autor" v-model="autor" placeholder="Agregar Autor">
      </div>
      <div class="formm-control formm-control-check">
        <label for="">Retirado</label>
        <input type="checkbox" v-model="retirado" name="retirado">
      </div>
      <div class="d-grid gap-2">
        <input type="submit" value="Guardar Libro" class="btn btn-primary">
      </div>
    </form>
  </template>

<script>
    export default{
        name: 'AddLibro',
        data(){
            return{
                nombre: '',
                autor: '',
                retirado: false
            }
        },
            methods:{
                onSubmit(e){
                    e.preventDefault()
                    if(!this.nombre){
                        alert("porfavor agregue un nombre para su libro")
                        return
                    }
                    
                    const newLibro = {
                        nombreLibro: this.nombre,
                        retirado: this.retirado,
                        autores: [
                            {
                                nombre: this.autor
                            }
                        ]
                    }

                    this.$emit('new-libro',newLibro)

                    this.nombre = ''
                    this.autor = ''
                    this.retirado = false

                }

            }
    }
</script>

<style scoped>
  .add-form{
    margin-bottom: 20px;
  }

  .formm-control{
    margin: 20px 0;
  }

  .formm-control label{
    display: block;
  }

  .formm-control input{
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
  }

  .formm-control-check{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .formm-control-check label{
    flex: 1;
  }

  .formm-control-check input{
    flex: 2;
    height: 20px;
  }
</style>