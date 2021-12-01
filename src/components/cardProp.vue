<template>
    <div class="card mb-3 border pointer">
        <!-- POSTER -->
        <div class="film-serie-poster">
            <img 
                class="poster"
                v-if="image !== null"
                :src="`https://image.tmdb.org/t/p/w342${image}`" :alt="`poster-${title}`"
            >
            <img 
                class="poster-error"
                v-else 
                src="../assets/poster-not-found.jpg" :alt="`poster-${title}`"
            >
        </div>
        <!-- INFO -->
        <div class="film-serie-info border d-none">
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
                <li class="d-flex">
                    <strong>Vote: </strong>
                    <span v-if="vote == 0">N.C.</span>
                    <div v-else class="vote-stars ms-1">
                        <i v-for="(n, i) in Math.ceil(vote/2)" :key="`star-${i}`" class="star fas fa-star"></i>
                        <i v-for="(n, i) in 5 - Math.ceil(vote/2)" :key="`starVoid-${i}`" class="star far fa-star"></i>
                    </div>
                </li>
                <li><strong>Trama: </strong>{{ plot }}</li>
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
        plot: String,
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
.card{
    width: 342px;
    position: relative;
    &:hover{
        .film-serie-info{
            display: block;
        }
    }
    .film-serie-info{
        position: absolute;
        top: 0;
        left: 0;
        height: 100%;
        background-color: rgba(0,0,0,0.5);
        color: white;
        strong{
            color: #ac1616;
        }
        .star{
            color: #d4d424;
        }
    }
}
ul{
    li{
        list-style: none;
        margin-top: 6px;
        img{
            width: 40px;
            height: 20px;
        }
    }
}
.poster{
    height: 100%;
}
.poster-error{
    width: 342px;
    height: 513px;
}
</style>