<template>
  <div>
    <h1> Entendiendo Modificadores de eventos</h1>

    <!-- <div id="abuelo"  @click="my_method('soy abuelo en bubbling')">
      Div Abuelo
      <div id="padre" @click.self.stop="my_method('hola Soy padre')">
        Div Padre
        <div id="hijo"  @click="my_method('hola Soy hijo')">
          Div Hijo
        </div>
      </div>
    </div> -->

    <form action="" >
      <label for="">Ingrese su nombre</label>
      <input type="text" v-model="name">
      <input type="submit" @click.prevent="form_send">
    </form>
  </div>
  
</template>

<script>
export default {
  name: 'event-component',
  // props: {},
  data: function(){
    return {
      name:"",
    }
  },
  // computed: {},
  methods: {
    // -- Metodos
    my_method(str){
      alert(str);
    },
    form_send(){
      alert("Formulario enviado por axios");
    }
  },
  // components: {},
}
</script>

<style scoped>
  #abuelo{
    background:grey;
    width: 300px;
    height: 300px;
    font-size:25px;
  }
  #padre{
    background: rgb(158, 147, 84);
    width: 200px;
    height: 200px;
    margin: 0 auto;
    position:relative;
    top:10%;
    font-size:25px;
  }
  #hijo{
    background: rgb(88, 88, 124);
    width:100px;
    height: 100px;
    margin:0 auto;
     position:relative;
    top:10%;
    font-size:20px;
  }

  a{
    color:white;
  }
</style>