<template>
  <div id="app" v-if="inLoad == true">

      <Head :dataFolder="selectContent" @update="upadatedArr"/>

    <div class="disco-box overflowy-scroll">
      <DiscoFolder :dataFolder="filterArr"/>
    </div>


  </div>
  <div class="loader" v-else>
    <img src="./assets/loader.svg" alt="">
    <p>Caricamento...</p>
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
      finded: 'All',
      inLoad: false
    }
  },

  methods: {
    upadatedArr: function(x){
      this.finded = x
      console.log(this.finded);
    }
  },

    computed: {
      filterArr: function(){
          if(this.finded == 'All') return this.selectContent
          return this.selectContent.filter(el => el.genre.toLowerCase() == this.finded.toLowerCase())

          
      },
    },

  mounted: function(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then(res => 
        this.selectContent = [...res.data.response]
    );
    setTimeout(()=>{
          this.inLoad = true
        }, 1500)
  },

}
</script>

<style lang="scss">
@import './components/style/general.scss';
@import './components/style/variables.scss';
@import './components/style/variables';

#app{
  height: 100vh;
  background-color: $bodyColor;
}

.disco-box{
  background-color: $bodyColor;
  padding-bottom: 50px;
}


.loader{
    width: 100%;
    height: 100vh;
    background-color: $bodyColor;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    p{
        font-size: 1.2rem;
        color:  $text;
        margin-top: 10px;
    }

    img{
        width: 10%;
        animation: 2s linear infinite spin
    }
}

@keyframes spin {
    from {rotate: 0deg;}
    to{rotate: 360deg}
}

</style>
