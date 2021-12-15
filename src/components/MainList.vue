<template>
<section class="d-flex border main-list" @mouseleave="returnOriginalBgColor">
              <!-- arrow-left -->
    <i 
        class="align-self-center me-1 fas fa-chevron-circle-left pointer" 
        v-show="arrayList.length > 5" 
        @click="scrollLeft"
    >
    </i>
              <!-- cards-list -->
    <div class="cards-list border d-flex" ref="list">
        <cardProp
            class="mx-1"
            v-for="el in arrayList" :key="el.id"
            :backgroundImage="el.backdrop_path"
            :image="el.poster_path"
            :title="el.title || el.name"
            :originalTitle="el.original_title || el.original_name"
            :lang="el.original_language"
            :vote="el.vote_average"
            :plot="el.overview"
        />
    </div>
              <!-- arrow-right -->
    <i 
        class="fas fa-chevron-circle-right align-self-center pointer ms-1" 
        v-show="arrayList.length > 5" 
        @click="scrollRight"
    >
    </i>
</section>
</template>

<script>
import cardProp from './cardProp.vue'
export default {
    name: 'MainList',
    components: {
        cardProp,
    },
    props:{
        arrayList: Array,
    },
    methods: {
        scrollRight(){
            this.$refs.list.scrollLeft += 500;
        },
        scrollLeft(){
            this.$refs.list.scrollLeft -= 500;
        },
        returnOriginalBgColor(){
            document.querySelector('#app').style.backgroundImage = "url('https://www.icolorpalette.com/download/solidcolorimage/141414_solid_color_background_icolorpalette.png')";
        }
    }

}

</script>

<style scoped lang="scss">
@import '@/style/utilities';
@import '@/style/variables';
    .main-list{
        .cards-list{
            overflow-x: scroll;
            &::-webkit-scrollbar {
                display: none;
            }
        }
        i{
            font-size: 50px;
            color: rgba(211, 211, 211, 0.582);
            transition: color .5s;
            &:hover{
                color: $primary-color;
            }
        }

    }
    /**********
    RESPONSIVE 
    ***********/
    /* desktop */
    /* tablet */
    @media  screen and (max-width: 768px) {
        .cards-list{
            padding: 0 30px;
        }
        .main-list i{
            display: none;
        }
        
    }
</style>