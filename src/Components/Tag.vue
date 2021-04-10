<template>
    <span class="tag" :class="tagColor">
      <span class="content">
        {{tag}}
      </span>
      <span @click="$emit('removeOneTag',index)" class="close">
        X
      </span>
    </span>
</template>

<script>
export default {
    props : ["tag","index","tagColor"]
}
</script>

<style scoped>
.success{
    background-color: blue;
}
.tag{
  background-color: #fbbd08;
  padding: 10px;
  color: #000;
  cursor: default;
  font-size: 14px;
  margin-right: 10px;
}
.close{
  font-size: 12px;
  cursor: pointer;
  color: #b80f0a;
}
</style>