<template>
            <div class="card col-3 m-4 p-3">
              <img :src="(imgQuery + imgSize + arname.poster_path === 'https://image.tmdb.org/t/p/w342/null') ? placeholder : imgQuery + imgSize + arname.poster_path" :alt="arname.title">  
              <h2>{{(arname.title) ? arname.title : arname.name}}</h2>
              <h3 v-if="(arname.orginal_title !== undefined && arname.orginal_title !== arname.title || arname.name !== undefined && arname.original_name !== arname.name)">
                  {{(arname.original_title) ? arname.original_title : arname.original_name}}</h3>
              <i :class="'flag flag-' + country(arname.original_language)" />
              <div class="stars">
                <i
                v-for="n in 5"
                :key="n"
                :class="(n <= stars(arname.vote_average)) ? 'fas fa-star' : 'far fa-star'"
                class="star"
                />
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
    .card{
        border-radius: 0px !important;
        background-color: rgb(37, 37, 37) !important;
    }
    .star{
        //display: inline;
        color: yellow;
    }
</style>