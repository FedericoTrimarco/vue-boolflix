<template>
    <div class="card mb-3">
        <div class="film-serie-poster">
            <img 
                v-if="image !== null"
                :src="`https://image.tmdb.org/t/p/w185${image}`" :alt="`poster-${title}`"
            >
            <img 
                v-else 
                src="../assets/error-404-no-wallpaper-found.png" :alt="`poster-${title}`" 
                class="poster-error"
            >
        </div>
        <div class="film-serie-info">
            <ul class="ms-1">
                <li><strong>Titolo: </strong>{{ title }}</li>
                <li><strong>Titolo Originale: </strong>{{ originalTitle }}</li>
                <li>
                    <strong>Lingua: </strong>
                    <img
                        v-if="flagLang"
                        :src="require(`../assets/boolflix-flags/${lang}.png`)" 
                        :alt="`${lang}-flag`"
                    >
                    <span v-else>{{ lang }}</span>
                </li>
                <li><strong>Voto:</strong> {{ vote }}</li>
            </ul>
        </div>
    </div>

</template>

<script>
export default {
    name: 'cardProp',
    props:{
        image: String,
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
            width: 40px;
            height: 20px;
        }
    }
}
.poster-error{
    width: 185px;
    height: 275px;
}
</style>