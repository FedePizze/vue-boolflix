<template>
  <div id="app">
    <MyHeader @ricercaFilm="getRisposta"></MyHeader>
    <MyMain :film="arrayFilm"></MyMain>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'

import axios from 'axios'

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },

  data() {
    return{
      arrayFilm: [],
      verifica: false
    }
  },

  methods: {
    getRisposta(ricerca) {
      this.verifica = true

      if (this.verifica == true) {
        axios.get("https://api.themoviedb.org/3/search/movie?api_key=86e1350e024b4487374d1c81a8d7c6db&query=" + ricerca + "&language=it-IT")

        .then(risultato => {
          this.arrayFilm = risultato.data.results;

          console.log(risultato.data.results);
        })

        .catch(error => {
          console.log(error);
        })
      }
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/style/general.scss";

</style>
