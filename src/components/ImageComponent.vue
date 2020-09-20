<template>
  <div>
    <h1> {{title_image}}</h1>
      <button @click="atras(id)">atras</button>
      <button @click="delante(id)">delante</button>
      <hr>
      <img :src='src_image' alt=''>
  </div>
</template>

<script>
export default {
  name: 'component-name',
  props: {
    title_image:{
      type: String,
      required: true,
    },
    src_image:{
      type: String,
      required:true,
    },
    id:{
      type:Number,
      required:true,
    }
  },
  data: function(){
    return {}
  },
  // computed: {},
  methods: {
    atras:function(id){
        this.$emit("atras",{id:id});
        //console.log(id);
    },
    delante:function(id){
      this.$emit("delante",{id:id});
    }
  },
  // components: {},
}
</script>

<style scoped>
  
</style>