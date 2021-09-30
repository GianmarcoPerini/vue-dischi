<template>
    <header>
        <div class="logo" @click="log(updateGenreData)">
            <img src="../assets/logo.png" alt="">
        </div>

        
        <GenreMenu :genre="getUniqueGenre()" @search="getFilterGenre" :filter="updateGenreData()"/>
        
        <ArtistMenu :artist="getUniqueArtist()"/>
        


    </header>
</template>

<script>
import GenreMenu from "./GenreMenu";
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
            find: '',
        }
    },

    methods:{

        getFilterGenre: function(x){
            this.find = x
        },

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

    computed: {
        updateGenreData: function(){
            return this.selectContent.filter(el => el.genre.toLowerCase().includes(this.find.toLowerCase()))
        },
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