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
    background: rgb(180,180,180);
background: linear-gradient(0deg, rgba(180,180,180,0.3113620448179272) 0%, rgba(116,116,116,0) 38%, rgba(161,1,1,0.8407738095238095) 98%);
    
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