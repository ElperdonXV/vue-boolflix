<template>
            <div class="card col-4">
              <img :src="(imgQuery + imgSize + arname.poster_path === 'https://image.tmdb.org/t/p/w500/null') ? placeholder : imgQuery + imgSize + arname.poster_path" :alt="arname.title">  
              <h2>{{(arname.title) ? arname.title : arname.name}}</h2>
              <h3>{{(arname.original_title) ? arname.original_title : arname.original_name}}</h3>
              <i :class="'flag flag-' + country(arname.original_language)" />
              <h4>{{arname.vote_average}}</h4>
              <h4>{{stars(arname.vote_average)}}</h4>
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
        imgSize: 'w500/',
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
    .star{
        //display: inline;
        color: yellow;
    }
</style>