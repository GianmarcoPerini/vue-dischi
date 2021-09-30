<template>
    <header>
        <div class="logo">
            <img src="../assets/logo.png" alt="">
        </div>

        <select name="genre" id="genre-select" class="ms-5">
            <option value="All">All</option>
            <GenreMenu v-for="(el, i) in getUniqueGenre()" :key="i" :genre="el"/>
        </select>

        <select name="artist" id="artist-select" class="ms-5" @click="getUniqueArtist()">
            <option value="All">All</option>
            <ArtistMenu v-for="(el, i) in getUniqueArtist()" :key="i" :artist="el"/>
        </select>


    </header>
</template>

<script>
import GenreMenu from "./SelectMenu";
import ArtistMenu from './ArtistMenu'
import axios from 'axios'
export default {
    name: 'Head',
    components: {
        GenreMenu,
        ArtistMenu,
    },
    data: function(){
        return{
            selectContent: [],
        }
    },

    methods:{
        getUniqueGenre: function(){
            let uniqueGenre = [];
            this.selectContent.forEach(el =>{
                if(uniqueGenre.indexOf(el.genre) == -1){
                    uniqueGenre.push(el.genre)
                }
            })
            return uniqueGenre
        },

        getUniqueArtist: function(){
            let uniqueArtist = [];
            this.selectContent.forEach(el =>{
                if(uniqueArtist.indexOf(el.author) == -1){
                    uniqueArtist.push(el.author)
                }
            })
            return uniqueArtist 
        },

        log: function(x){
            console.log(x);
        }
    },

    mounted: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music').then(res => {
            this.selectContent = [...res.data.response]
        });
    }

}
</script>

<style lang="scss" scoped>
@import './style/variables';
header{
    padding: 8px;
    background-color: $headerColor;
    margin-bottom: 50px;
    display: flex;
    align-items: center;

    .logo{
        width: 50px;
        height: 50px;

        img{
            width: 100%;
        }
    }
}

</style>