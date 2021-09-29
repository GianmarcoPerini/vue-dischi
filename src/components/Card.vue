<template>
    <div class="single-card">
        <div class="img-box mb-4">
            <img :src="poster" alt="">
        </div>
        <div class="info text-center">
            <h4 class="text-white mb-4">{{title}}</h4>
            <p class="m-0">{{author}}</p>
            <p class="m-0">{{year}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props:{
        poster: String,
        title: String,
        author: String,
        genre: String,
        year: String,
    }

}
</script>

<style lang="scss">
@import './style/variables.scss';

.single-card{
    width: 100%;
    aspect-ratio: 1/1.7;
    background-color: $cardColor;
    padding-top: 20px;

    p{
        color: $text;
    }

    .img-box{
    width: 80%;
    margin: 0 auto;
    aspect-ratio: 1/1;

        img{
        width: 100%;
        height: 100%;
        object-fit: fill;
        }
    }
}



</style>