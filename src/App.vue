<template>
  <div id="app">

      <Head />
    <div class="disco-box">
      <DiscoFolder />
    </div>


  </div>
</template>

<script>
import Head from './components/Head.vue'
import DiscoFolder from './components/DiscoFolder.vue'


export default {
  name: 'App',
  components: {
    Head,
    DiscoFolder,
  },

}
</script>

<style lang="scss">
@import './components/style/general.scss';
@import './components/style/variables.scss';
@import './components/style/variables';

#app{
  // height: calc(100vh );
  background-color: $bodyColor;
}

.disco-box{
  // display: flex;
  // justify-content: center;
  // align-items: center;
  background-color: $bodyColor;
  // height: calc(100% - 66px);
}
</style>
