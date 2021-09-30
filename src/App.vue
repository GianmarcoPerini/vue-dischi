<template>
  <div id="app">

      <Head :dataFolder="selectContent" @update="upadatedArr"/>
    <div class="disco-box">
      <DiscoFolder :dataFolder="filterArr"/>
    </div>


  </div>
</template>

<script>
import Head from './components/Head.vue'
import DiscoFolder from './components/DiscoFolder.vue'
import axios from 'axios'


export default {
  name: 'App',
  components: {
    Head,
    DiscoFolder,
  },
  data: function(){
    return{
      selectContent: [],
      filterArr: [],
    }
  },

  methods: {
    upadatedArr: function(x){
      this.filterArr = x
      console.log(this.filterArr);
    }
  },

  mounted: function(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then(res => 
        this.selectContent = [...res.data.response]
    );
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
