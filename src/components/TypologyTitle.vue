<template>
    <div class="tv-movie-list d-flex justify-content-center align-items-center my-4">
        <img src="../assets/small-logo.png" alt="small-logo">
        <h1 class="text-white ms-1" v-show="mainArray.length !== 0">{{text}}</h1>
    </div>
</template>

<script>
export default {
    name: 'TypologyTitle',
    props: {
        mainArray: Array,
        text: String,
    }
}
</script>

<style scoped lang="scss">
@import '@/style/utilities';
.tv-movie-list{
  text-align: center;
  margin: 50px 0;
  letter-spacing: 5px;
}
</style>