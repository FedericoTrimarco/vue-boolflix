<template>
    <header class="border text-white">
        <div class="container d-flex justify-content-between align-items-center">
                       <!-- logo -->
            <div class="d-flex align-items-center">
                <img src="../assets/Boolflix-logo.png" alt="logo">
                       <!-- link-list -->
                <ul class="d-flex ms-1 list-none">
                    <li v-for="(link, id) in linkList" :key="id">
                        <a href="/" @click.prevent>{{link}}</a>
                    </li>
                </ul>
            </div>
                        <!-- search bar -->
            <div class="search">
                <input 
                    v-model.trim="searchFilmSeries"
                    type="text"
                    placeholder="search movie / series"
                    @keyup.enter="$emit('search', searchFilmSeries), clearInput()"
                >
                <i 
                    class="pointer fs-1 fas fa-search" 
                    @click="$emit('search', searchFilmSeries), clearInput()"
                >
                </i>
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
            linkList: ['Home','Serie Tv','Film','Nuovi e popolari','La mia lista'],
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
    background: linear-gradient(
                                    0deg,
                                    rgba(20,20,20,0) 9%,
                                    rgba(20,20,20,0.8911939775910365) 46%,
                                    rgba(0,0,0,1) 100%
                                );
    position: fixed;
    z-index: 1;
    width: 100%;
    padding-top: 15px;
    
    li{
        margin-left: 40px;
        a{
            text-decoration: none;
            font-weight: bold;
            color: #ffffffc5;
            &:hover{
                color: #ffffff79;
            }
            &:focus{
                color: #fff;
            }
        }
    }
    input{
        height: 35px;
        padding-right: 150px;
        margin-right: 10px;
        border: none;
        color: white;
        background-color: transparent;
        outline: none;
        border-bottom: 1px solid white;
        &:focus{
            border-bottom: 1px solid $primary-color;
        }
    }
}
</style>