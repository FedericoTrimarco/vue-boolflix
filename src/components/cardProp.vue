<template>
    <div class="card mb-3 border pointer">
        <!-- POSTER -->
        <div class="film-serie-poster">
            <img 
                v-if="image !== null"
                class="poster"
                :src="`https://image.tmdb.org/t/p/w342${image}`" :alt="`poster-${title}`"
            >
            <img 
                v-else 
                class="poster-error"
                src="../assets/poster-not-found.jpg" :alt="`poster-${title}`"
            >
        </div>
        <!-- INFO -->
        <div class="film-serie-info border d-none" tabindex="0">
            <ul class="ms-1">
                <li class="text-center mb-4">
                    <i class="arrow fas fa-chevron-up"></i>
                    <h1>{{ title }}</h1>
                </li>
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
                <li class="d-flex align-items-center">
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
    position: relative;
    overflow: hidden;
    &:hover{
        .film-serie-info{
            display: block;
        }
    }
    .film-serie-poster{
        .poster{
            height: 513px;
        }
        .poster-error{
            width: 342px;
            height: 513px;
        }
    }
    .film-serie-info{
        position: absolute;
        left: 0;
        bottom: 0;
        width: 100%;
        height: 100px;
        background-color: rgba(0,0,0,0.8);
        color: white;
        transition: height .5s;
        &:focus{
            height: 100%;
            .arrow{
                transform: rotate(180deg);
            }
        }
        strong{
            color: #ac1616;
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
        .star{
            color: #d4d424;
        }
    }
}
</style>