<template>
    <header>
        <div class="logo" @click="log(updateGenreData)">
            <img src="../assets/logo.png" alt="">
        </div>

        
        <GenreMenu :genre="getUniqueGenre()" @search="getFilterGenre" />
        
        <ArtistMenu :artist="getUniqueArtist()"/>
        


    </header>
</template>

<script>
import GenreMenu from "./GenreMenu";
import ArtistMenu from './ArtistMenu'

export default {
    name: 'Head',
    props:['dataFolder'],
    components: {
        GenreMenu,
        ArtistMenu,
    },
    data: function(){
        return{
            find: '',
        }
    },

    methods:{

        getFilterGenre: function(x){
            this.find = x
        },

        getUniqueGenre: function(){
            let uniqueGenre = [];
            this.dataFolder.forEach(el =>{
                if(uniqueGenre.indexOf(el.genre) == -1){
                    return uniqueGenre.push(el.genre)
                }
            })
            return uniqueGenre
        },

        getUniqueArtist: function(){
            let uniqueArtist = [];
            this.dataFolder.forEach(el =>{
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
            if(this.find == 'All') return this.dataFolder
            
            return this.dataFolder.filter(el => el.genre.toLowerCase().includes(this.find.toLowerCase()))
        },
    },



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