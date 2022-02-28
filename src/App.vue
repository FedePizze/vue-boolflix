<template>
  <div id="app">
    <MyHeader @ricercaFilm="getRisposta" :generi="altro" @genereScelto='getGenere'></MyHeader>
    <MyMain :film="arrayFilm" :genere="portingGenere"></MyMain>
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

      genereFilm: [],
      fine: [],
      altro: [],
      verifica: false,
      portingGenere: 0
    }
  },

  methods: {
    getRisposta(ricerca) {
      this.verifica = true
      this.genereFilm = []
      this.fine = []
      this.altro = []

      if (this.verifica == true) {
        axios.get("https://api.themoviedb.org/3/search/movie?api_key=86e1350e024b4487374d1c81a8d7c6db&query=" + ricerca + "&language=it-IT")

        .then(risultato => {
          this.arrayFilm = risultato.data.results;

          
          //console.log(risultato.data.results);

          for(let i = 0; i < this.arrayFilm.length; i++) {

            if(!this.genereFilm.includes(this.arrayFilm[i].genre_ids)) {

              this.genereFilm.push(this.arrayFilm[i].genre_ids);
              
            }
          }
          console.log(this.genereFilm)

          var merged = [].concat.apply([], this.genereFilm);
          this.fine = merged
          console.log(this.fine)

          for(let i = 0; i < this.fine.length; i++) {

            if(!this.altro.includes(this.fine[i])) {

              this.altro.push(this.fine[i]);
            }
          }
          console.log(this.altro)
            
        })

        .catch(error => {
          console.log(error);
        })
      }
    },

    getGenere(genere) {

      if(genere == "Avventura") {
        this.portingGenere = 12
      } else if (genere == "Fantascenza") {
        this.portingGenere = 878
      } else if (genere == "Famiglia") {
        this.portingGenere = 10751
      } else if (genere == "Animazione") {
        this.portingGenere = 16
      } else if (genere == "Commedia") {
        this.portingGenere = 35
      } else if (genere == "Fantasy") {
        this.portingGenere = 14
      } else if (genere == "Thriller") {
        this.portingGenere = 53
      } else if (genere == "Dramma") {
        this.portingGenere = 18 
      } else if (genere == "Romance") {
        this.portingGenere = 10749
      } else if (genere == "Horror") {
        this.portingGenere = 27
      }


      console.log(this.portingGenere)
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/style/general.scss";

</style>
