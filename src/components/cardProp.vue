<template>

    <ul class="ms-1 mt-3">
        <li><strong>Titolo:</strong> {{ title }}</li>
        <li><strong>Titolo Originale:</strong> {{ originalTitle }}</li>
        <li v-if="flagLang">
            <img :src="require(`../assets/boolflix-flags/${lang}.png`)" :alt="`${lang}-flag`">
        </li>
        <li v-else><strong>Lingua:</strong> {{ lang }}</li>
        <li><strong>Voto:</strong> {{ vote }}</li>
    </ul>

</template>

<script>
export default {
    name: 'cardProp',
    props:{
        title: String,
        originalTitle: String,
        lang: String,
        vote: Number,
    },
    data(){
        return{
            arrLanguages: ['it', 'en']
        }
    },
    computed:{
        flagLang(){
            return this.arrLanguages.includes(this.lang);
        }
    }
}
</script>

<style scoped lang="scss">
@import '@/style/utilities';
ul{
    li{
        margin-top: 6px;
        img{
            width: 60px;
            height: 30px;
        }
    }
}
</style>