<template>
  <div class="container">
    <TitleElement msg="Get Pokemons API "/>
    <input 
      v-model="txtPokemon"
      class="fieldTxt" 
      type="text" 
      placeholder="Poker Name"
    >
    <button class="btn" >Search</button>
  </div>
</template>

<script>
  import TitleElement from './components/TitleElement.vue'

  export default {
    name: 'App',
    components: {
      TitleElement
    },

    data(){
      return {
        pokerApi: [],
        txtPokemon: "",
        baseUrl: "https://pokeapi.co/api/v2/"
      }
    },
    
    methods: {
    getIndividualPokemon(){
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokerName}`)
      .then(response => response.json())
      .then(data => {
        console.log(data);
        this.pokemons = [];
        this.pokemons.push(data)
        })
      }
    }
  }

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f2f6fa;
  margin-top: 60px;
  font-size: 20px;
}
.container {
  margin: 0 auto;
  background-color: #2c3e50;
  width: 500px;
  height: 170px;
  box-shadow: 0 8px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 40px 0 rgba(0, 0, 0, 0.19);
}
.fieldTxt {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 200px;
  height: 20px;
  margin: 10px;
  border: solid 1px #2c3e50;
}
.btn {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  border: solid 1px #2c3e50;
  width: 120px;
  height: 25px;
  color: white;
  background-color: rgb(20, 130, 219);
}
.btn:hover {
  background-color: rgb(46, 155, 243);
}
</style>
