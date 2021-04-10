<template>
    <div class="tag-container">
    <Tag v-for="(tag,index) in tags" :key="index" :tag="tag" :index="index" @removeOneTag="removeOneTag($event)" :tagColor ="color"/>
    <input type="text" @keydown.enter="addTag" @keydown.backspace="removeTag">
    <p class="error" v-if="error">This tags added before</p>
  </div>
</template>

<script>
import Tag from './Tag'
export default {
    components : {
        Tag
    },
    data(){
    return{
      tags : [],
      error : false
    }
  },
  props : {
      value : {
          required : false
      },
      color : {
          type : String,
          required :false,
          default : "primary"
      }
  },
  created(){
      if(this.value){
          if(this.value.length > 0){
              this.tags = this.value.split(",")
          }
      }
  },
  methods : {
    addTag(event){
      let val  = event.target.value
      let matchedTag = false
      if(val.length > 0){
          this.tags.forEach(element => {
            if(element.toLowerCase() === val.toLowerCase()){
              matchedTag = true
              this.error = true
            }
          });
      }
      if(!matchedTag){
        this.tags.push(val)
      }else{
        this.error = true
        setTimeout(()=>{
          this.error = false
        },2000)
      }
      event.target.value = ''
    },
    removeTag(event){
      if(event.target.value.length == 0){
        this.tags.splice(this.tags.length-1,1)
      }
    },
    removeOneTag(index){
      this.tags.splice(index,1)
    }
  },
  watch : {
      tags(){
          this.$emit("input",this.tags.join(","))
      }
  }
   
  
}
</script>

<style scoped>
.tag-container{
 border: 1px solid #ccc;
 padding: 20px;
}

input{
  outline: none;
  width: 100px;
  height: 50px;
}

.error{
  color: red;
  font-size: 12px;
  margin-top: 5px;
}
</style>