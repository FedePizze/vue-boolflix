<template>
  

  <div class="flip-card" v-for="(elemento, index) in generiFiltrati" :key="index.id">

    <div class="flip-card-inner">

      <div class="flip-card-front">
        <img class="copertinaFilm" :src="'https://image.tmdb.org/t/p/w780/' + elemento.poster_path" alt="Poster Image">
      </div>

      <div class="flip-card-back">
        
        <h4><span class="titolo">Titolo:&nbsp;</span>{{elemento.original_title}}</h4>

        <h4 class="lingua" v-if="elemento.original_language == 'en' "><span class="titolo">Lingua: </span> <img class="flag" src="../../assets/img/gb.svg" alt=""></h4>
        <h4 class="lingua" v-else-if="elemento.original_language == 'it' "><span class="titolo">Lingua: </span> <img class="flag" src="../../assets/img/it.svg" alt=""></h4>
        <h4 class="lingua" v-else><span class="titolo">Lingua:&nbsp;</span>{{elemento.original_language}}</h4>
        
        <h4 v-if="elemento.vote_average >= 0 && elemento.vote_average <= 2"><span class="titolo">Voto:&nbsp;</span>&starf;</h4>
        <h4 v-else-if="elemento.vote_average > 2 && elemento.vote_average <= 4"><span class="titolo">Voto:&nbsp;</span>&starf;&starf;</h4>
        <h4 v-else-if="elemento.vote_average > 4 && elemento.vote_average <= 6"><span class="titolo">Voto:&nbsp;</span>&starf;&starf;&starf;</h4>
        <h4 v-else-if="elemento.vote_average > 6 && elemento.vote_average <= 8"><span class="titolo">Voto:&nbsp;</span>&starf;&starf;&starf;&starf;</h4>
        <h4 v-else><span class="titolo">Voto:&nbsp;</span>&starf;&starf;&starf;&starf;&starf;</h4>
        

        <h4 class="overview"><span class="titolo">Overview:</span><br>{{elemento.overview}}</h4>
      </div>
    </div>
  </div>
  
</template>

<script>
export default {
  name: "FilmCard",
  props: {
    dati: Array,
    datiGenere: Number
  },

  methods: {
    // &starf;

  },

  created() {
    console.log(this.dati)
  },

  computed: {
    generiFiltrati() {
      if (!this.datiGenere == 0) {

        return this.dati.filter(item => {
        return item.genre_ids.includes(this.datiGenere)
        });
        
      } else {

        return this.dati
      }
    }
  }

}
</script>

<style scoped lang="scss">
  .flip-card{
    width: calc(100% / 4);
    height: 600px;
    padding: 10px;
    background-color: transparent;
    perspective: 1000px;
    color: white;

    .flip-card-inner{
      width: 100%;
      background-color: black;
      position: relative;
      height: 100%;
      transition: transform 0.6s;
      transform-style: preserve-3d;

      h4{
        padding: 5px 0;
        font-weight: 400;
      }

      .titolo{
        font-weight: 800;
      }

      .lingua{
        display: flex;
        align-items: center;
      }

      .flag{
      width: 25px;
      margin-left: 10px;
      }

      .overview{
        overflow-y: auto;
        height: 450px;
      }
    }

    .flip-card-back {
    color: white;
    transform: rotateY(180deg);
    padding: 20px;
    }

    .flip-card-front {
    background-color: #bbb;
    }

    .flip-card-front, .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    }

    .copertinaFilm{
    width: 100%;
    height: 100%;
    object-position: auto;
    }
    
  }

  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  

  
  
</style>