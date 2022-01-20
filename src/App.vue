<template>
  <div id="app">
    <Header 
       @emitSearch="getCard($event)"
    />
    <Main :cards="cards"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    Header,
    Main,
},
data(){
        return {
        queryPath: 'https://api.themoviedb.org/3/search/',
        queryKey: '6a1be3e2f2a8c68b3ee64e9d5b7d296b',
        textSearch: '',
        cards: null,
        arrayFilm: null,
        arraySeries: null,
    };
},
watch:{
  printCard(){
    this.callMovies();
    this.callSeries();
    this.mergeArray();
  }
},

 methods: {
        
        callMovies(){
          this.arrayFilm = null;
          const movie = 'movie';
          const parametri= {
            api_key: this.queryKey,
            query: this.textSearch
          }
            axios.get(`${this.queryPath}${movie}`, { params: parametri }
            ).then((result)=>{
                this.arrayFilm = result.data.results;
                console.log(result.data.results);
            }).catch((error)=>{
                console.log(error);
            });
        },

        callSeries(){
          this.arraySeries = null;
          const tv = 'tv';
          const parametri= {
            api_key: this.queryKey,
            query: this.textSearch
          }
            axios.get(`${this.queryPath}${tv}`, { params: parametri }
            ).then((result)=>{
                this.arraySeries = result.data.results;
                console.log(result.data.results);
            }).catch((error)=>{
                console.log(error);
            });
        },

        getCard(text){
            if (text != '') {
            this.textSearch = text;
        }
        },

        mergeArray(){
          this.cards = [...this.arrayFilm, ...this.arraySeries];
        },
}, 
}
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap";
</style>
