<template>
  

  <div class="flip-card" v-for="(elemento, index) in dati" :key="index.id">

    <div class="flip-card-inner">

      <div class="flip-card-front">
        <img class="copertinaFilm" :src="'https://image.tmdb.org/t/p/w780/' + elemento.poster_path" alt="Poster Image">
      </div>

      <div class="flip-card-back">
        
        <h4><span class="titolo">Titolo:</span>{{elemento.original_title}}</h4>

        <h4 class="lingua" v-if="elemento.original_language == 'en' "><span class="titolo">Lingua: </span> <img class="flag" src="../../assets/img/gb.svg" alt=""></h4>
        <h4 class="lingua" v-else-if="elemento.original_language == 'it' "><span class="titolo">Lingua: </span> <img class="flag" src="../../assets/img/it.svg" alt=""></h4>
        <h4 class="lingua" v-else><span class="titolo">Lingua:&nbsp;</span>{{elemento.original_language}}</h4>
        
        <h4><span class="titolo">Voto:&nbsp;</span>{{elemento.vote_average}}</h4>

        <h4 class="overview"><span class="titolo">Overview:</span><br>{{elemento.overview}}</h4>
      </div>
    </div>
  </div>
  
</template>

<script>
export default {
  name: "FilmCard",
  props: {
    dati: Array
  },

  methods: {
    
  },

  created() {
    console.log(this.dati)
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
    
  }

  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
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
    object-position: top;
  }

  h4{
    padding: 5px 0;
  }

  

  
    
</style>