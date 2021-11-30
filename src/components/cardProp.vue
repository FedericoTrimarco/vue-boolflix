<template>

    <ul v-if="title != '' || name != ''" class="ms-1 mt-3">
        <li><strong>Titolo:</strong> {{ title }}{{ name }}</li>
        <li><strong>Titolo Originale:</strong> {{ originalTitle }}{{ originalName }}</li>
        <li>
            <strong>Lingua:</strong>
            <img
                v-if="flagLang"
                :src="require(`../assets/boolflix-flags/${lang}.png`)" 
                :alt="`${lang}-flag`"
            >
            <span v-else>{{ lang }}</span>
        </li>
        <li><strong>Voto:</strong> {{ vote }}</li>
    </ul>

</template>

<script>
export default {
    name: 'cardProp',
    props:{
        title: String,
        name: String,
        originalTitle: String,
        originalName: String,
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
            width: 50px;
            height: 20px;
        }
    }
}
</style>