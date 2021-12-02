<template>
<section class="d-flex">

    <i class="align-self-center me-1 fas fa-chevron-circle-left pointer" v-show="arrayList.length > 5" @click="scrollRight"></i>
    <div class="cards-list border d-flex" ref="list">
        <cardProp
            class="mx-1"
            v-for="el in arrayList" :key="el.id"
            :image="el.poster_path || el.poster_path"
            :title="el.title || el.name"
            :originalTitle="el.original_title || el.original_name"
            :lang="el.original_language || el.original_language"
            :vote="el.vote_average || el.vote_average"
            :plot="el.overview"
        />
    </div>
    <i class="fas fa-chevron-circle-right align-self-center pointer ms-1" v-show="arrayList.length > 5" @click="scrollLeft"></i>
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
        scrollLeft(){
            this.$refs.list.scrollLeft += 2000;
        },
        scrollRight(){
            this.$refs.list.scrollLeft -= 2000;
        }
    }

}

</script>

<style scoped lang="scss">
@import '@/style/utilities';
@import '@/style/variables';
.cards-list{
    overflow-x: scroll;
    &::-webkit-scrollbar {
        display: none;
    }
}
i{
    font-size: 50px;
    color: rgb(211, 211, 211, 0.15);
    transition: color .5s;
    &:hover{
        color: $primary-color;
    }
}
</style>