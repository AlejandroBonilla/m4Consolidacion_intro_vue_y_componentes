<template>
  
    <form action="">
      <label for="">Nombre Foto</label>
      <input type="text" ref="type_photo" v-model="type_photo"><br>
      <label for="">Link Foto</label>
      <input type="text"  v-model="link_photo" class="link_input"><br>
      <input type="submit" @click.prevent="agregar_imagen" value="Agregar Foto">
    </form>
  
</template>

<script>
export default {
  name: 'Form-Img',
  // props: {},
  data: function(){
    return {
      type_photo:"",
      link_photo:"",
    }
  },
  // computed: {},
  methods: {
    agregar_imagen(){
      if(this.type_photo === "" || this.link_photo === ""){
        alert("Campos sin rellenar");
        return;
      }

      let new_imagen = {
        type_photo : this.type_photo,
        link_photo : this.link_photo,
      }

      this.$emit("agregar_img",new_imagen);
      this.cleanInputs();

    },
    cleanInputs(){
      this.type_photo = "";
      this.link_photo = "";
      this.$refs.type_photo.focus()
    
    }
  },
  // components: {},
}
</script>

<style scoped>
  form{
    width: 30%;
    border:2px solid rgb(47, 129, 47);
    padding:10px;
    border-radius: 10px;
    font-size:1.2rem;
  }
  label{
    display:inline-block;
    width:130px;
  }
  input[type="submit"]{
    display:inline-block;
    border:none;
    color:white;
    background: rgb(54, 149, 54);
    padding: 7px;
    border-radius:5px;
    margin-top:10px;
    width: 200px;
    
  }
  .link_input{
    width: 25rem;
  }

</style>