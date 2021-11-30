<template>
    <header class="container">
            <input 
                v-model.trim="searchFilmSeries" 
                type="text" 
                placeholder="search movie / series" 
                @keyup.enter="$emit('search', searchFilmSeries), clearInput()"
            >
            <button @click="$emit('search', searchFilmSeries), clearInput()">Invio</button>
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
    padding-top: 15px;
    display: flex;
    input{
        height: 35px;
        padding-right: 150px;
        margin-right: 10px;
    }
    button{
        border: none;
        padding: 10px 40px;
        cursor: pointer;
    }
}
</style>