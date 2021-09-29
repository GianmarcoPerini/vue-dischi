<template>
    <div class="container">
        <div v-if="inLoad == true" class="row row-cols-xl-5 row-cols-lg-4 row-cols-md-3 row-cols-sm-2 row-cols-1 g-4">
            <div class="col" v-for="(el, index) in cardContent" :key="index">
                <Card :poster="el.poster" :title="el.title" :author="el.author" :genre="el.genre" :year="el.year"/>
            </div>
        </div>
        <div class="loader" v-else>
            <img src="../assets/loader.svg" alt="">
            <p>Caricamento...</p>
        </div>
        
    </div>
</template>

<script>
import Card from './Card.vue';
import axios from "axios";

export default {


    name: 'DiscoFolder',
    components:{
        Card,

    },
    data: function(){
    return{
        cardContent: [],
        inLoad: false
    }
},

    mounted: function(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res => {
    this.cardContent = res.data.response
    setTimeout(()=>{
        this.inLoad = true
    },1500)
    });
}

}
</script>

<style lang="scss">
@import './style/variables';


.loader{
    width: 100%;
    height: 100vh;
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