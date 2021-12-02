<template>
    <header class="border text-white">
        <div class="container d-flex justify-content-between align-items-center">
            <img src="../assets/Boolflix-logo.png" alt="logo">
            <div class="search">
                <input 
                    v-model.trim="searchFilmSeries" 
                    type="text" 
                    placeholder="search movie / series" 
                    @keyup.enter="$emit('search', searchFilmSeries), clearInput()"
                >
                <i class="pointer fs-1 fas fa-search" @click="$emit('search', searchFilmSeries), clearInput()"></i>
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
@import '@/style/variables';

header{
    background: rgb(20,20,20);
    background: linear-gradient(0deg, rgba(20,20,20,0.8911939775910365) 46%, rgba(195,39,39,1) 100%);
    
    position: fixed;
    z-index: 1;
    width: 100%;
    padding-top: 15px;
    input{
        height: 35px;
        padding-right: 150px;
        margin-right: 10px;
        border: none;
        color: white;
        background-color: rgba(0,0,0,0.0001);
        outline: none;
        border-bottom: 1px solid white;
        &:focus{
            border-bottom: 1px solid $primary-color;
        }
    }
}
</style>