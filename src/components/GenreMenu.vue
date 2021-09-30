<template>
    
        <select name="genre" id="genre-select" class="ms-5" @change="$emit('search', filtro)" v-model="filtro">

            <option value="All" >All</option>

            <option v-for="(el, i) in genre" :key="i" :value="el" > {{el}} </option>
        </select>
    
</template>

<script>
export default {
    name: 'SelectionMenu',
    props: ['genre'],

    data: function(){
        return{
            filtro: '',
        }
    },

    methods: {


        genreFilter: function(){

        },

        ret: function(x){
            return x
        },

        log: function(x){
            console.log(x);
        }
    },

    computed: {

    }
}
</script>

<style>

</style>