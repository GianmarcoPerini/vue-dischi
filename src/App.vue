<template>
  <div id="app">

      <Head />

      <DiscoFolder />


  </div>
</template>

<script>
import axios from 'axios'
import Head from './components/Head.vue'
import DiscoFolder from './components/Head.vue'


export default {
  name: 'App',
  components: {
    Head,
    DiscoFolder,
  },
  data: function(){
    return{
      cardContent: [],
    }
  },

  mounted: function(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res => {
    this.cardContent = res.data.response
    });
  }
}
</script>

<style lang="scss">
@import './components/style/general.scss';
@import './components/style/variables.scss';
@import './components/style/variables';

#app{
  height: calc(100vh );
  background-color: $bodyColor;
}
</style>
