<template>
    <header class="border">
        <div class="container d-flex justify-content-between align-items-center">
            <img src="../assets/Boolflix-logo.png" alt="logo">
            <div class="search">
                <input 
                    v-model.trim="searchFilmSeries" 
                    type="text" 
                    placeholder="search movie / series" 
                    @keyup.enter="$emit('search', searchFilmSeries), clearInput()"
                >
                <i class="fs-1 fas fa-search" @click="$emit('search', searchFilmSeries), clearInput()"></i>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            searchFilmSeries: '',
        }
    },
    methods: {
        clearInput(){
            this.searchFilmSeries = '';
        }
    }
}
</script>

<style scoped lang="scss">
@import '@/style/utilities';

header{
    background: rgb(0,0,0);
    background: linear-gradient(0deg, rgba(0,0,0,0.927608543417367) 0%, rgba(111,0,0,0.8743872549019608) 55%, rgba(255,0,0,0.76234243697479) 100%);
    
    position: fixed;
    z-index: 1;
    width: 100%;
    padding-top: 15px;
    input{
        height: 35px;
        padding-right: 150px;
        margin-right: 10px;
    }
}
</style>