<template>
  <div class="container">
      <div class="row row-col-3">
          <Card
          v-for="(film, index) in cards.film"
          :key="index"
          :arname="film"
          />
          <Card
          v-for="(serie, index) in cards.series"
          :key="index"
          :arname="serie"
          />
        </div>
  </div>
</template>

<script>
import Card from './Card.vue';
export default {
    name: 'Main',
    components:{
        Card,
    },
    props: {
    cards: Array,
    },
}
</script>
<style lang="scss">
</style>