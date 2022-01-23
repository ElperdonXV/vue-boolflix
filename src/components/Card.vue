<template>
            <div class="card col-3 m-4 p-3">
                <div class="content">
                    <div class="image">
                        <img :src="(imgQuery + imgSize + arname.poster_path === 'https://image.tmdb.org/t/p/w342/null') ? placeholder : imgQuery + imgSize + arname.poster_path" :alt="arname.title">
                    </div>
                    <div class="description">
                        <h2>{{(arname.title) ? arname.title : arname.name}}</h2>
                        <h3 v-if="(arname.orginal_title !== undefined && arname.orginal_title !== arname.title || arname.name !== undefined && arname.original_name !== arname.name)">
                        {{(arname.original_title) ? arname.original_title : arname.original_name}}</h3>
                        <i :class="'flag flag-' + country(arname.original_language)" />
                        <div class="stars" :title="'Voto:' + ' ' + arname.vote_average">
                            <i
                                v-for="n in 5"
                                :key="n"
                                :class="(n <= stars(arname.vote_average)) ? 'fas fa-star' : 'far fa-star'"
                                class="star"
                            />
                        </div>
                    </div>
                </div>
            </div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css';
export default {
name: 'Card',
data(){
    return{
        imgQuery: 'https://image.tmdb.org/t/p/',
        imgSize: 'w342/',
        placeholder: 'https://cdn.download.it/ms/static/images/poster-placeholder.png',
    }
}, 
props: {
    arname: {
        type: Object,
    }
},
methods: {
    country(nation){
        if (nation === 'en'){
            return 'us';
        }
        else if (nation === 'ja'){
            return 'jp';
        }
        return nation;
    },
    stars(nstar){
        return Math.round(nstar / 2);
    }
} 
}
</script>

<style lang="scss">
@import '~mdb-ui-kit/css/mdb.min.css';
    .content{
        position: relative;
        width: 100%;
        height: 100%;
        .description{
            position: absolute;
            top: 0;
            left: 0;
            z-index: 2;
            width: 100%;
            height: 100%;
            background-color: rgba($color: #444444, $alpha: 0.9);
            opacity: 0;
        }
    }
    .card:hover .description{
            opacity: 100;
        }
    .image{
        width: 100%;
        img{
            width: 100%;
        }
    }
    .card{
        border-radius: 0px !important;
        background-color: black !important;
    }
    .star{
        //display: inline;
        color: yellow;
    }
</style>