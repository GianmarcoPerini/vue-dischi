<template>
    <div class="single-card-box">
        <div class="card-img-oiu">
            <img :src="poster" alt="">
        </div>
        <p class="text-white text-center">{{title}}</p>
        <p class="m-0 text-secondary">{{author}}</p>
        <p class="m-0 text-secondary">{{year}}</p>
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


.single-card-box{
    width: 90%;
    min-height: 255px;
    min-height: 300px;
    background-color: $cardColor;
    display: flex;
    align-items: center;
    padding-top: 15px;
    flex-direction: column;
    margin-bottom: 10px;


    .card-img-oiu{
        width: 90%;
        aspect-ratio: 1/1;
        margin-bottom: 10px;
        overflow: hidden;

        img{
            width: 100%;
            height: 100%;

        }
    }
}

</style>