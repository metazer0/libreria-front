
<template>
  <Nav/>
  <RouterView />
</template>

<script>
import Nav from './components/Nav.vue';

export default{
    name: 'App',
    components: {
      Nav,
    }
  }

</script>
