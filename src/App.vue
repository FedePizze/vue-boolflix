<template>
  <div id="app">
    <MyHeader @ricercaFilm="getRisposta" @ricercaSerie="getRispostaSerie"         :generi="pushFinale"         @genereScelto='getGenere'></MyHeader>
    <MyMain :film="arrayFilm" :serie="arraySerie" :genere="portingGenere"></MyMain>
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
      arraySerie: [],

      genereFilm: [],
      genereSerie: [],

      fine: [],
      fineSerie: [],

      altro: [],
      altroSerie: [],

      iGeneri: [],
      tuttiGeneri: [],

      pushFinale: [],

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

      this.pushFinale = []

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

          for(let i = 0; i < this.fine.length; i++) {

            if(!this.altro.includes(this.fine[i])) {

              this.altro.push(this.fine[i]);
            }
          }
            
        })

        .catch(error => {
          console.log(error);
        })
      }
    },

    getRispostaSerie(ricerca) {
      this.verifica = true
      this.genereSerie = []

      this.fineSerie = []
      this.altroSerie = []

      this.iGeneri = []
      this.tuttiGeneri = []

      this.pushFinale = []



      if (this.verifica == true) {
        axios.get("https://api.themoviedb.org/3/search/tv?api_key=86e1350e024b4487374d1c81a8d7c6db&query=" + ricerca + "&language=it-IT")

        .then(risultato => {
          this.arraySerie = risultato.data.results;

          

          for(let i = 0; i < this.arraySerie.length; i++) {

            if(!this.genereSerie.includes(this.arraySerie[i].genre_ids)) {

              this.genereSerie.push(this.arraySerie[i].genre_ids);
              
            }
          }

          var merged = [].concat.apply([], this.genereSerie);
          this.fineSerie = merged

          for(let i = 0; i < this.fineSerie.length; i++) {

            if(!this.altroSerie.includes(this.fineSerie[i])) {

              this.altroSerie.push(this.fineSerie[i]);
            }
          }

          this.iGeneri = [this.altro, this.altroSerie]

          var newMerged = [].concat.apply([], this.iGeneri);
          this.tuttiGeneri = newMerged
          console.log(this.tuttiGeneri)

          for(let i = 0; i < this.tuttiGeneri.length; i++) {

            if(!this.pushFinale.includes(this.tuttiGeneri[i])) {

              this.pushFinale.push(this.tuttiGeneri[i]);
            }
          }
            
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
      } else if (genere == "Azione") {
        this.portingGenere = 28
      } else if (genere == "Crime") {
        this.portingGenere = 80
      } else if (genere == "Documentario") {
        this.portingGenere = 99
      } else if (genere == "Storia") {
        this.portingGenere = 36
      } else if (genere == "Musica") {
        this.portingGenere = 10402
      } else if (genere == "Mistero") {
        this.portingGenere = 9648
      } else if (genere == "Tv Movie") {
        this.portingGenere = 10770
      } else if (genere == "Guerra") {
        this.portingGenere = 10752
      } else if (genere == "Western") {
        this.portingGenere = 37
      } else if (genere == "Kids") {
        this.portingGenere = 10762
      } else if (genere == "News") {
        this.portingGenere = 10763
      } else if (genere == "Reality") {
        this.portingGenere = 10764
      } else if (genere == "Sci-Fi") {
        this.portingGenere = 10765
      } else if (genere == "Soap Opera") {
        this.portingGenere = 10766
      } else if (genere == "Talk Show") {
        this.portingGenere = 10767
      } else if (genere == "Politica") {
        this.portingGenere = 10768
      } else if (genere == "Alta Tensione") {
        this.portingGenere = 10759
      } else {
        this.portingGenere = 0
      }

      console.log(this.portingGenere)
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/style/general.scss";

</style>
