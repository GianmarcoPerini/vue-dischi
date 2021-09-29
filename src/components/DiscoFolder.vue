<template>
    <div class="container w-75">
        <div class="row row-cols-5">
            <div class="col" v-for="(el, index) in cardContent" :key="index">
                <Card :poster="el.poster" :title="el.title" :author="el.author" :genre="el.genre" :year="el.year"/>
            </div>
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


div{
    width: 100%;

}
</style>