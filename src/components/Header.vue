<template>
    <header class="border container">
            <input v-model.trim="searchFilm" type="text" placeholder="search movie" @keyup.enter="$emit('search', searchFilm)">
            <button @click="$emit('search', searchFilm)">Invio</button>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            searchFilm: '',
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