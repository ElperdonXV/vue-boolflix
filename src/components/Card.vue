<template>
            <div class="card col-4">
              <img :src="imgQuery + imgSize + arname.poster_path" alt="">  
              <h2>{{(arname.title) ? arname.title : arname.name}}</h2>
              <h3>{{(arname.original_title) ? arname.original_title : arname.original_name}}</h3>
              <i :class="'flag flag-' + country(arname.original_language)" />
              <h4>{{arname.vote_average}}</h4>
            </div>
</template>

<script>
export default {
name: 'Card',
data(){
    return{
        imgQuery: 'https://image.tmdb.org/t/p/',
        imgSize: 'w500/',
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
    }
} 
}
</script>

<style lang="scss">
@import '~mdb-ui-kit/css/mdb.min.css';
</style>