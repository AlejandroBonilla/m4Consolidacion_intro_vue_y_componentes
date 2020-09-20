<template>
  <div>
    <h1> Nuevo Componente</h1>
    <event-component></event-component>
    <gallery-component></gallery-component>
  </div>
  
</template>

<script>
 import EventosComponent from "./components/Eventos.vue";
 import GalleryComponent from "./components/GalleryComponent.vue";
export default {
  name: 'app-component',
  // props: {},
  data: function(){
    return {}
  },
  // computed: {},
  methods: {
    // -- Metodos
  },
  components: {
    'event-component':EventosComponent, 
    'gallery-component':GalleryComponent,
  },
}
</script>

<style scoped>
  
</style>