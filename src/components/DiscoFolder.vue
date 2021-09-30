<template>
    <div class="container">
        <div class="row row-cols-xl-5 row-cols-lg-4 row-cols-md-3 row-cols-sm-2 row-cols-1 g-4">
            <div class="col" v-for="(el, index) in dataFolder" :key="index">
                <Card :poster="el.poster" :title="el.title" :author="el.author" :genre="el.genre" :year="el.year"/>
            </div>
        </div>
        
        
    </div>
</template>

<script>
import Card from './Card.vue';


export default {


    name: 'DiscoFolder',
    props: ['dataFolder'],
    components:{
        Card,
    },
    data: function(){
    return{

    }
},

}
</script>

<style lang="scss">
@import './style/variables';





</style>