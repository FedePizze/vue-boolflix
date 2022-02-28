<template>
  <div id="mainBox">

      
    <h1 v-if="this.film == '' "></h1>
    <h1 v-else>FILM</h1>
    <div id="filmRow">
        <FilmCard :dati="film" :datiGenere="genere"></FilmCard>
    </div>

    <h1 v-if="this.serie == '' "></h1>
    <h1 v-else>SERIE TV</h1>
    <div id="filmRow">
        <FilmCard :dati="serie" :datiGenere="genere"></FilmCard>
    </div>

  </div>
</template>

<script>
import FilmCard from "./partials/FilmCard.vue"

export default {
    name: "MyMain",
    props: {
        film: Array,
        serie: Array,
        genere: Number
    },

    components: {
        FilmCard
    }
}
</script>

<style scoped lang="scss">
    #mainBox{
        min-height: 90vh;
        background-color: rgb(94, 94, 94);

        #filmRow{
            display: flex;
            flex-wrap: wrap;
            padding: 0px 50px;
            margin-bottom: 30px;
        }

        h1{
            margin-left: 60px;
            padding: 40px 0px 0px 0px;
            color: white;
            font-size: 60px;
        }
    }
</style>