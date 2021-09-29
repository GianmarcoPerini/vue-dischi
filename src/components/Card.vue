<template>
    <div class="single-card-box">
        <div class="card-img-oiu">
            <img :src="poster" alt="">
        </div>
        <h4 class="text-white text-center mt-4">{{title}}</h4>
        <div class="info text-center mt-2">
            <p class="m-0 text-secondary">{{author}}</p>
            <p class="m-0 text-secondary">{{year}}</p>
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


.single-card-box{
    // width: 90%;

    min-height: 450px;
    background-color: $cardColor;
    display: flex;
    align-items: center;
    padding-top: 15px;
    padding-bottom: 20px;
    flex-direction: column;
    margin-bottom: 10px;

    p{
        font-size: 1.1rem;
    }

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