<template>
  <div id="cardBox" v-for="(elemento, index) in dati" :key="index.id">
    <div id="card">
      <h4>{{elemento.original_title}}</h4>
      <h4>{{elemento.original_language}}</h4>
      <h4>{{elemento.vote_average}}</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmCard",
  props: {
    dati: Array
  },

  created() {
    console.log(this.dati)
  }
}
</script>

<style scoped lang="scss">
  #cardBox{
    width: calc(100% / 4);
    padding: 10px;

    #card{
      width: 100%;
      padding: 10px;
      background-color: aqua;
    }
  }
    
</style>