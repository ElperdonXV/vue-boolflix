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
        queryPath: 'https://api.themoviedb.org/3/search/movie',
        queryKey: '6a1be3e2f2a8c68b3ee64e9d5b7d296b',
        textSearch: '',
        cards: null,
    };
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
  @import "~bootstrap/scss/bootstrap";
</style>
