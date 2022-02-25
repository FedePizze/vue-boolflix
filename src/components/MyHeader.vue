<template>
  <div id="headerBox">
      <h1>BOOLFLIX</h1>
      <div id="searchBox">
          <input v-model="ricerca" @keyup.enter="aggiungiRicerca()" type="text">
          <button @click="aggiungiRicerca()">CERCA</button>
      </div>
  </div>
</template>

<script>
export default {
    name: "MyHeader",

    data() {
        return{
            ricerca: '',
            datoDaInviare: []
        }
    },

    methods: {
        aggiungiRicerca() {
            console.log(this.ricerca)

            this.$emit('ricercaFilm', this.ricerca)
        }
    }
}

</script>

<style scoped lang="scss">
    #headerBox{
        height: 10vh;
        background-color: black;
        display: flex;
        justify-content: space-between;
        align-items: center;

        h1{
            font-weight: 700;
            color: red;
            margin-left: 30px;
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