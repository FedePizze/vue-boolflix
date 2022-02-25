<template>
  <div id="mainBox">
      <div id="filmRow">
          <FilmCard :dati="film"></FilmCard>
      </div>
  </div>
</template>

<script>
import FilmCard from "./partials/FilmCard.vue"

export default {
    name: "MyMain",
    props: {
        film: Array
    },

    components: {
        FilmCard
    },

    data() {
        return{
            datiFilm: []
        }
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
        }
    }
</style>