<template>
  <div id="headerBox">
        <div id="logoBox">

            <h1>BOOLFLIX</h1>

            <select id="select" @change="filtraGenere($event)">
                <option value="Tutti i generi"><h5>TUTTI I GENERI</h5></option>
                <option v-for="(elemento, index) in generi" :key="index.id">
                    <h5 v-if="elemento == 12" href="">Avventura</h5>
                    <h5 v-else-if="elemento == 28" href="">Azione</h5>
                    <h5 v-else-if="elemento == 10759" href="">Alta Tensione</h5>
                    <h5 v-else-if="elemento == 878" href="">Fantascenza</h5>
                    <h5 v-else-if="elemento == 10751" href="">Famiglia</h5>
                    <h5 v-else-if="elemento == 16" href="">Animazione</h5>
                    <h5 v-else-if="elemento == 35" href="">Commedia</h5>
                    <h5 v-else-if="elemento == 14" href="">Fantasy</h5>
                    <h5 v-else-if="elemento == 53" href="">Thriller</h5>
                    <h5 v-else-if="elemento == 18" href="">Dramma</h5>
                    <h5 v-else-if="elemento == 10749" href="">Romance</h5>
                    <h5 v-else-if="elemento == 27" href="">Horror</h5>
                    <h5 v-else-if="elemento == 80" href="">Crime</h5>
                    <h5 v-else-if="elemento == 99" href="">Documentario</h5>
                    <h5 v-else-if="elemento == 36" href="">Storia</h5>
                    <h5 v-else-if="elemento == 10402" href="">Musica</h5>
                    <h5 v-else-if="elemento == 9648" href="">Misteri</h5>
                    <h5 v-else-if="elemento == 10770" href="">TV Movie</h5>
                    <h5 v-else-if="elemento == 10752" href="">Guerra</h5>
                    <h5 v-else-if="elemento == 37" href="">Western</h5>
                    <h5 v-else-if="elemento == 10762" href="">Kids</h5>
                    <h5 v-else-if="elemento == 10763" href="">News</h5>
                    <h5 v-else-if="elemento == 10764" href="">Reality</h5>
                    <h5 v-else-if="elemento == 10765" href="">Sci-Fi</h5>
                    <h5 v-else-if="elemento == 10766" href="">Soap Opera</h5>
                    <h5 v-else-if="elemento == 10767" href="">Talk Show</h5>
                    <h5 v-else-if="elemento == 10768" href="">Politica</h5>
                </option>
            </select>

        </div>
      
        <div id="searchBox">
            <input v-model="ricerca" @keyup.enter="aggiungiRicerca()" type="text">
            <button @click="aggiungiRicerca()">CERCA</button>
            <button @click="reload()">NUOVA RICERCA</button>
        </div>
  </div>
</template>

<script>
export default {
    name: "MyHeader",
    props: {
        generi: Array,
    },

    data() {
        return{
            ricerca: '',
            genere: '',
            generiCount: 0,
        }
    },

    methods: {
        aggiungiRicerca() {
            console.log(this.ricerca)

            this.$emit('ricercaFilm', this.ricerca)
            this.$emit('ricercaSerie', this.ricerca)
        },

        reload() {
            location.reload();
        },

        filtraGenere($event) {
            this.genere = ''
            this.genere = $event.target.value
            console.log($event.target.value)

            this.$emit('genereScelto', this.genere)
        }
    },

    mounted() {
        this.$emit('genereScelto', this.genere)
    },
}

</script>

<style scoped lang="scss">
    #headerBox{
        height: 10vh;
        background-color: black;
        display: flex;
        justify-content: space-between;
        align-items: center;
        
        #logoBox{
            display: flex;
            align-items: center;

            h1{
            font-weight: 700;
            color: red;
            margin: 0px 30px;
            }

            select{
                padding: 5px 20px;
                border-radius: 5px;
                background-color: white;
            }

            option{
                color: red;
                font-size: 15px;
                font-weight: bold;
                text-transform: uppercase;
            }

            h5{
                text-align: center;
                height: 20px;
                margin-right: 10px;
            }
        }

        #searchBox{
            margin-right: 30px;

            input{
            padding: 6px;
            border-radius: 6px;
            }

            button{
                padding: 6px;
                background-color: red;
                color: white;
                border-radius: 6px;
                font-weight: 700;
                margin-left: 10px;
            }
        }
    }

</style>