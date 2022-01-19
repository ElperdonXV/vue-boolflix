<template>
  <div class="container">
      <input type="text" v-model="textSearch" @keyup.enter="sendSearch()">
  </div>
</template>

<script>
export default {
    name: 'Search',
    data(){
        return{
            textSearch:'',
        };
    },
    methods: {
        sendSearch(){
            console.log(this.textSearch);
            this.$emit('emitSearch', this.textSearch);
        },
    },
}
</script>

<style lang="scss">

</style>