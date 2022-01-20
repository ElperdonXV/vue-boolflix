<template>
  <div class="container">
      <div class="row">
          <div v-for="(card, index) in cards" :key="index" class="cards col">
            <div class="card">
              <h2>{{card.title}}</h2>
              <h3>{{card.original_title}}</h3>
              <h4>{{card.original_language}}</h4>
              <h4>{{card.vote_average}}</h4>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Main',
    data(){
    
},
props: {
    cards: Array,
}
}
</script>
<style lang="scss">
</style>