<template>
  <div>
    <form-component @agregar_img="agregar_img"></form-component>
    <image-component 
      v-for="image in gallery" 
      :key="image.id"
      class="img_comp"
      :title_image="image.title"
      :src_image="image.src"
      :id="image.id"
      @atras="atras_img"
      @delante="delante_img"
      @eliminar="eliminar_img"
    >
    </image-component>

  </div>

  
</template>

<script>
import FormImgComponent from "./Form_img.vue";
import ImageComponent from "./ImageComponent.vue";
export default {
  name: 'gallery-component',
  // props: {},
  data: function(){
    return {
      gallery:[
          {id:1,title:"Sport", src:"https://picsum.photos/id/684/200/200"},
          {id:2,title:"cat", src:"https://picsum.photos/id/685/200/200"},
          {id:3,title:"Food", src:"https://picsum.photos/id/686/200/200"},
          {id:4,title:"City", src:"https://picsum.photos/id/687/200/200"},
        ]
    }
  },
  // computed: {},
  methods: {
    // -- Metodos
    atras_img(e){
      let id = e.id;
      let index = this.gallery.findIndex((image)=>image.id === id);

      if(index>0){
        let new_index = index - 1;
        let index_ant = index;

        let new_gallery = [...this.gallery];
        new_gallery[new_index] = this.gallery[index];
        new_gallery[index_ant] = this.gallery[new_index];
        this.gallery = [...new_gallery];
      }
      else{
        let img = this.gallery[index];
        this.gallery.splice(index,1);
        this.gallery.push(img);
      }
    },
    delante_img(e){

      let id = e.id;
      let index = this.gallery.findIndex((image)=>image.id === id);

      if(this.gallery[index+1]== undefined){
        let img = this.gallery[index];
        this.gallery.splice(index,1);
        this.gallery = [img, ...this.gallery]
      }
      else{
        let new_index = index + 1;
        let index_pos = index;

        let new_gallery = [...this.gallery];

        new_gallery[new_index] = this.gallery[index];
        new_gallery[index_pos] = this.gallery[new_index];
        this.gallery = [...new_gallery];

      }
    },
    agregar_img(newImg){
    
      let img ={
        id: this.new_id(),
        src: newImg.link_photo,
        title: newImg.type_photo,
      }

      this.gallery.push(img);

    },
    new_id(){
      let new_id = parseInt((Math.random()*100));
      let result = this.gallery.some((img)=>img.id ===new_id);

      while(result == true){
        new_id = parseInt((Math.random()*100));
        result = this.gallery.some((img)=>img.id === new_id);
      }

      return (new_id);
    },
    eliminar_img(e){
      let id = e.id;

      let index = this.gallery.findIndex((img)=>img.id === id);

      this.gallery.splice(index,1);

    }

  },
  components: {
    'image-component':ImageComponent,
    'form-component':FormImgComponent,
  },
}
</script>

<style scoped>
  .img_comp{
      display: inline-block;
      border:3px solid grey;
      text-align: center;
      border-radius: 5px;
    }
    .img_comp > h1{
      font-weight: bolder;
      font-size:30px;
      
      padding:5px;
    }
</style>