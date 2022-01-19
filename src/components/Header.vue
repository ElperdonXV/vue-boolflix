<template>
  <header>
    <div class="container">
      <input type="text" v-model="textSearch" @keyup.enter="sendSearch()">
  </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
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
  header{
    padding: 20px;
    background-color: black;
  }
</style>