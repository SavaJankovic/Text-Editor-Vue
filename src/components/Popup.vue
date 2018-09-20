<template>
  <div id="popup" >
    <span class="close" @click="$emit('close')">X</span>
    <div  class="text-box" v-html="text" :class="'size' + size" >

    </div>

  </div>
</template>

<script>


export default {
  name: 'Popup',
  props: ['size', 'text']
}


</script>


<style scoped>
  #popup { display: block; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color:silver; color: #000; overflow: scroll; z-index: 2;}

  .close { position: absolute; top: 20px; right: 20px; color: #000; font-size: 30px; cursor: pointer; }
  .text-box{margin: auto; }
  .size13 { width: 100%; max-width: 1024px;  margin-top: 50px;}
  .size17 { width: 100%; max-width: 1680px; margin-top: 50px; }
  .size40 { width: 100%; max-width: 2560px; margin-top: 50px; }
</style>
