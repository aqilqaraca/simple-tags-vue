<template>
  <div>
    <Taglar v-model="tags" color="success" />
  {{tags}}
  </div>
</template>

<script>
import Taglar from './Components/Taglar'
export default {
  components : {
    Taglar
  },
  data(){
    return{
      tags : "deneme,test,salam,menim,adim,aqildir,senin,adin,nedir"
    }
  }
  
}
</script>

<style>
body{
  font-family: sans-serif;
}

</style>