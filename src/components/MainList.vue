<template>
    <section class="container mt-3 border">
        <cardProp
            v-for="el in arrayList" :key="el.id"
            :image="el.poster_path || el.poster_path"
            :title="el.title || el.name"
            :originalTitle="el.original_title || el.original_name"
            :lang="el.original_language || el.original_language"
            :vote="el.vote_average || el.vote_average"
        />
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
    }
}

</script>

<style scoped lang="scss">
@import '@/style/utilities';

</style>