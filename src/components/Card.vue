<template>
            <div class="card col-4">
              <h2>{{(arname.title) ? arname.title : arname.name}}</h2>
              <h3>{{(arname.original_title) ? arname.original_title : arname.original_name}}</h3>
              <i :class="'flag flag-' + country(arname.original_language)" />
              <h4>{{arname.original_language}}</h4>
              <h4>{{arname.vote_average}}</h4>
            </div>
</template>

<script>
export default {
name: 'Card',
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
        return nation;
    }
} 
}
</script>

<style lang="scss">
@import '~mdb-ui-kit/css/mdb.min.css';
</style>