<template>
    <header class="border text-white">
        <div class="container d-flex justify-content-between align-items-center">
                       <!-- logo -->
            <div class="d-flex align-items-center logo">
                <img src="../assets/Boolflix-logo.png" alt="logo">
                       <!-- link-list -->
                <ul class="d-flex ms-1 list-none">
                    <li v-for="(link, id) in linkList" :key="id">
                        <a href="/" @click.prevent="$emit('click', link)">{{link}}</a>
                    </li>
                </ul>
            </div>
            <!-- mini-logo -->
            <div class="mini-logo d-none">
                <div class="d-flex align-items-center border justify-content-between">
                    <i class="fas fa-bars" @click="showCategories()"></i>
                    <img src="../assets/small-logo.png" alt="small-logo" class="w-50 ">
                </div>
                    
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
        <div class="categories" ref="categories">
            <div>
                <h1>CATEGORIES</h1>
                <ul class="list-none">
                    <li v-for="(link, id) in linkList" :key="id" class="my-1">
                        <a href="/" @click.prevent="$emit('click', link), showCategories()">{{link}}</a>
                    </li>
                </ul>
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
            linkList: ['Home','Serie Tv','Film'],
        }
    },
    methods: {
        clearInput(){
            this.searchFilmSeries = '';
        },
        showCategories(){
            document.querySelector('.categories').classList.toggle("active")
        }
    },
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
        .categories{
            background: #000;
            height: 0px;
            overflow: hidden;
            transition: height 0.5s;
            div{
                padding-left: 70px;
                padding-top: 50px;
                h1{
                    color: $primary-color
                }
            }
            &.active{
                height: 100vh;
            }
        }
    }
    /**********
    RESPONSIVE 
    ***********/
    /* desktop */
    @media  screen and (max-width: 1400px) {
        
    }
    /* tablet */
    @media  screen and (max-width: 768px) {
        .logo{
            display: none;
        }
        .mini-logo  {
            display: block;
            &:hover{
                ul{
                    display: block
                }
            }
        }
        
    }
</style>