<template>
  <div class="container">
      <Search
        @emitSearch="getCard($event)" 
      />
      <div v-for="(card, index) in cards" :key="index" class="cards">
          <div class="card">
              {{card.original_title}}
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';
import Search from './Search.vue';
export default {
    name: 'Main',
    data(){
        return {
        queryPath: 'https://api.themoviedb.org/3/search/movie',
        queryKey: '6a1be3e2f2a8c68b3ee64e9d5b7d296b',
        textSearch: '',
        cards: null,
    };
},
    components: {
        Search,
    },
    methods: {
        getCard(text){
            this.textSearch = text;
            this.card = null;
            axios.get(
                this.queryPath, {
                    params: {
                        api_key: this.queryKey,
                        query: this.textSearch,
                    }
                }
            ).then((result)=>{
                this.cards = result.data.results;
                console.log(result.data.results);
            }).catch((error)=>{
                console.log(error);
            });
        },
}, 
}
</script>

<style lang="scss">

</style>