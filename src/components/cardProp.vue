<template>
    <div class="card mb-2 border" @mouseleave="removeInfo">
        <!-- POSTER -->
        <div class="film-serie-poster pointer">
            <img 
                v-if="image !== null"
                class="poster border"
                :src="`https://image.tmdb.org/t/p/original${image}`" :alt="`poster-${title}`"
            >
            <img 
                v-else 
                class="poster-error"
                src="../assets/poster-not-found.jpg" :alt="`poster-${title}`"
            >
        </div>
        <!-- INFO -->
        <div 
            :class="{active : active == true}" 
            class="film-serie-info border d-none h-100px"
        >
            <ul class="ms-1">
                <li class="text-center mb-4">
                    <i class="arrow mb-1 fs-1 pointer fas fa-chevron-up" @click="showInfo"></i>
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
                    <strong>Vote:</strong>
                    <span v-if="vote == 0">N.C.</span>
                    <div v-else class="vote-stars ms-1">
                        <i 
                            v-for="(n, i) in Math.ceil(vote/2)" 
                            :key="`star-${i}`" 
                            class="star fas fa-star"
                        >
                        </i>
                        <i 
                            v-for="(n, i) in 5 - Math.ceil(vote/2)" 
                            :key="`starVoid-${i}`" 
                            class="star far fa-star"
                        >
                        </i>
                    </div>
                </li>
                <li>
                    <strong>Trama: </strong>
                    <span v-if="plot === ''">non disponibile</span>
                    <span v-else class="line-height-25">{{ plot }}</span>
                </li>
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
            arrLanguages: ['it', 'en'],
            active: false,
        }
    },
    computed:{
        flagLang(){
            return this.arrLanguages.includes(this.lang);
        }
    },
    methods:{
        showInfo(){
            this.active = !this.active;
        },
        removeInfo(){
            this.active = false;
        }
    }

}
</script>

<style scoped lang="scss">
@import '@/style/utilities';
@import '@/style/variables';
.card{
    border-radius: 20px;
    position: relative;
    overflow: hidden;
    min-width: 342px;
    max-width: 342px;
    &:hover{
        .film-serie-info{
            display: block;
        }
    }
    .film-serie-poster{
        height: 100%;
        img{
            transition: filter 1.5s;
        }
        .poster{
            height: 100%;
            width: 100%;
            object-fit: cover;
        }
        .poster-error{
            width: 100%;
            height: 100%;
        }
        &:hover{
            img{
                filter: blur(.5rem);;
            }
        }
    }
    .film-serie-info{
        position: absolute;
        left: 0;
        bottom: 0;
        width: 100%;
        background-color: rgba(0,0,0,0.7);
        color: white;
        transition: height .5s;
        strong{
            color: $primary-color;
        }
        li{
            list-style: none;
            margin-top: 6px;
            img{
                width: 40px;
                height: 20px;
            }
            
        }
        .star{
            color: #d4d424;
        }
    }
}
</style>