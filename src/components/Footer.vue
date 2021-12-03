<template>
  <footer class="pt-5">
    <div class="d-flex justify-content-center">

        <ul class="list-none mb-3 border" v-for="(el, id) in linkFooter" :key="id">
            <h3 class="text-white mb-3">{{el.title}}</h3>
            <li v-for="(link, id) in el.linkList" :key="id" class="mb-1">
                <a href="/" @click.prevent>{{link}}</a>
            </li>
            <li v-for="(social, id) in el.linkSocial" :key="id" class="mb-1 d-flex border">
                <a href="/" @click.prevent>
                    <i :class="`${social}`" class="fs-2"></i>
                </a>
            </li>
        </ul>

    </div>
    <p class="text-center text-white">made with <span>&hearts;</span> by Federico</p>

  </footer>
</template>

<script>
export default {
    name: 'Footer',
    data(){
        return{
            linkFooter: [
                {
                    title: 'CHI SIAMO',
                    linkList: ['Federico Trimarco', 'BoolFlix', 'Boolean']
                },
                {
                    title: 'COSA OFFRIAMO',
                    linkList: ['Centro assistenza', 'Opportunità di lavoro', 'Preferenze per i coockie', 'Carte regalo']
                },
                {
                    title: 'CONTATTACI',
                    linkList: ['via Ferrovia 16', 'Napoli','081 4563782',]
                },
                {
                    title: 'I NOSTRI SOCIAL',
                    linkSocial: ['fab fa-instagram','fab fa-linkedin','fab fa-facebook-square']
                }
            ]
        }
    }
}
</script>

<style scoped lang="scss">
@import '@/style/utilities';
@import '@/style/variables';
footer{
    background-color: #141414f1;
    border-top: 1px solid #ffffff23;
    // margin-top: 50px;
    padding: 50px;
    div{
        margin: 0 auto;
        ul{
            width: (100% / 6);
            a{
                color: #ffffff79;
                text-decoration: none;
                &:hover{
                    text-decoration: underline;
                    color: $primary-color;
                }
            }
        }
    }
    p{
        letter-spacing: 5px;
        span{
            color: $primary-color;
            font-size: 30px;
            margin: 0 10px;
        }
    }
    
}
</style>