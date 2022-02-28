<template>
  <div id="headerBox">
        <div id="logoBox">

            <h1>BOOLFLIX</h1>

            <select id="select" @change="filtraGenere($event)">
                <option value="">Scegli un genere</option>
                <option v-for="(elemento, index) in generi" :key="index.id">
                    <h5 v-if="elemento == 12" href="">Avventura</h5>
                    <h5 v-else-if="elemento == 28" href="">Azione</h5>
                    <h5 v-else-if="elemento == 878" href="">Fantascenza</h5>
                    <h5 v-else-if="elemento == 10751" href="">Famiglia</h5>
                    <h5 v-else-if="elemento == 16" href="">Animazione</h5>
                    <h5 v-else-if="elemento == 35" href="">Commedia</h5>
                    <h5 v-else-if="elemento == 14" href="">Fantasy</h5>
                    <h5 v-else-if="elemento == 53" href="">Thriller</h5>
                    <h5 v-else-if="elemento == 18" href="">Dramma</h5>
                    <h5 v-else-if="elemento == 10749" href="">Romance</h5>
                    <h5 v-else-if="elemento == 27" href="">Horror</h5>
                </option>
            </select>

        </div>
      
        <div id="searchBox">
            <input v-model="ricerca" @keyup.enter="aggiungiRicerca()" type="text">
            <button @click="aggiungiRicerca()">CERCA</button>
        </div>
  </div>
</template>

<script>
export default {
    name: "MyHeader",
    props: {
        generi: Array
    },

    data() {
        return{
            ricerca: '',
            genere: '',
            generiCount: 0
        }
    },

    methods: {
        aggiungiRicerca() {
            console.log(this.ricerca)

            this.$emit('ricercaFilm', this.ricerca)
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

            .fa-solid {
                width: 20px;
                height: 20px;
                color: white;
            }

            #generiBoxActive{
                display: block;
            }

        }

        #searchBox{
            margin-right: 30px;

            input{
            padding: 6px;
            border-radius: 6px;
            margin-right: 10px;
            }

            button{
                padding: 6px;
                background-color: red;
                color: white;
                border-radius: 6px;
                font-weight: 700;
            }
        }
    }

</style>