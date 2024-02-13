<!-- modulo para renderizar libro -->

<template>
  <div>
    <h3>
      {{ libro.nombreLibro }}
      <i @click="onDelete(libro.id)" class="fas fa-times"></i>
      <i class="fa fa-pencil" aria-hidden="true"></i>
    </h3>
    <p>{{ libro.autores }}</p>
  </div>
</template>

<script>
export default {
  name: "Libro",
  props: {
    libro: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-libro", id);
    }
  },
};
</script>

<style>
.fas {
  color: red;
  padding-top: 10px;
  margin-right: 10px;
}

.fa-bookmark {
  color: steelblue;
}
</style>
