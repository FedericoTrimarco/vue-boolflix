<template>
    <header class="border container">
        <form>
            <input v-model.trim="searchMovie" type="text" placeholder="search movie">
            <button>Invio</button>
        </form>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            searchMovie: '',
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