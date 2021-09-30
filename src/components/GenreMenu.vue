<template>
    
        <select name="genre" id="genre-select" class="ms-5">
            <option value="All" @click="$emit( 'search', ret('All'))">All</option>
            <option v-for="(el, i) in genre" :key="i" value="" @click="$emit( 'search', ret(el))"> {{el}} </option>
        </select>
    
</template>

<script>
export default {
    name: 'SelectionMenu',
    props: ['genre'],

    data: function(){
        return{


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