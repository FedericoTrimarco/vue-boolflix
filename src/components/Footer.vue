<template>
    <footer class="pt-5">
        <div class="d-flex flex-wrap justify-content-center container-2">

            <ul class="list-none mb-3 border link-list" v-for="(el, id) in linkFooter" :key="id">
                <h3 class="text-white mb-3">{{el.title}}</h3>
                <li v-for="(link, id) in el.linkList" :key="id" class="mb-1">
                    <a href="/" @click.prevent>{{link}}</a>
                </li>
                <li v-for="(social, id) in el.linkSocial" :key="id" class="social mb-1 border">
                    <a :href="social.path" target="_blank">
                        <i :class="`${social.icon}`" class="fs-2"></i>
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
                    linkList: ['Centro assistenza', 'Opportunità di lavoro', 'Carte regalo']
                },
                {
                    title: 'CONTATTACI',
                    linkList: ['via Ferrovia 16', 'Napoli','081 4563782',]
                },
                {
                    title: 'I NOSTRI SOCIAL',
                    linkSocial: [
                        {
                            icon: 'fab fa-instagram',
                            path: 'https://www.instagram.com/fede.trimarco/'
                        },
                        {
                            icon: 'fab fa-linkedin',
                            path: 'https://www.linkedin.com/in/federico-trimarco-85923a228/'
                        },
                        {
                            icon: 'fab fa-facebook-square',
                            path: 'https://www.facebook.com/federico.trimarco.7'
                        },
                    ]
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
        padding: 50px;
        div{
            margin: 0 auto;
            ul{
                width: (100% / 4);
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
    /**********
    RESPONSIVE 
    ***********/
    /* tablet */
    @media  screen and (max-width: 1200px) {
        .link-list{
            width: calc(100% / 2);
            .social{
                display: inline-block;
                margin-right: 10px;
            }
        }
    }
    /* small-tablet */
    @media  screen and (max-width: 639px) {
        .link-list{
            display: flex;
            flex-direction: column;
            align-items: center;
            width: calc(100% / 1);
            .social{
                display: inline-block;
            }
        }
    }
    @media  screen and (max-width: 500px) {
        p{
            display: none;
        }
        
    }
</style>