<template>
    <div class="container">
        <div v-if="inLoad == true" class="row row-cols-xl-5 row-cols-lg-4 row-cols-md-3 row-cols-sm-2 row-cols-1 g-4">
            <div class="col" v-for="(el, index) in cardContent" :key="index">
                <Card :poster="el.poster" :title="el.title" :author="el.author" :genre="el.genre" :year="el.year"/>
            </div>
        </div>
        <div class="d-none" v-else></div>
        
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
    },1000)
    });
}

}
</script>

<style lang="scss">


div{
    width: 100%;

}
</style>