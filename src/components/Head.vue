<template>
    <header>
        <div class="logo">
            <img src="../assets/logo.png" alt="">
        </div>
    </header>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@import './style/variables';
header{
    padding: 8px;
    background-color: $headerColor;
    margin-bottom: 50px;

    .logo{
        width: 50px;
        height: 50px;

        img{
            width: 100%;
        }
    }
}

</style>