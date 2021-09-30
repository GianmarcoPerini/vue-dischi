<template>

        <!-- <option value="">{{artist}}</option> -->
        <select name="artist" id="artist-select" class="ms-5">
            <option value="All" @click="log(ret('All'))">All</option>
            <option v-for="(el, i) in artist" :key="i" value="" @click="log(el)"> {{el}} </option>
        </select>
    
</template>

<script>
export default {
    name: 'ArtistMenu',
    props: ['artist'],
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
    

}
</script>

<style>

</style>