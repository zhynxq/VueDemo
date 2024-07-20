<template>
  <div class="app">
    <MyHreader></MyHreader>
    <MyBoby></MyBoby>
  </div>
  
</template>

<script>
import MyHreader from './components/MyHreader.vue';
import MyBoby from './components/MyBoby.vue'
export default {
  components:{
    MyHreader,
    MyBoby
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
  background-color: #f6f6f6;
}

</style>