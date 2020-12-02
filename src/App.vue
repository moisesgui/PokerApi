<template>

  <div class="container">
    <TitleElement msg="Get Pokemons API " />
    <div class="content-select">
      <select class="select-element" name="Select Search">
        <option class="opSelect" value="Select">Select Search</option>
        <option class="opName" value="Name">Name</option>
        <option class="opId" value="Id">Id</option>
        <option class="opAbility" value="Ability">Ability</option>
      </select>
      <button class="btn" @click="getPokerApi()">Search</button>
    </div>
  </div>

</template>

<script>
import TitleElement from "./components/TitleElement.vue";

export default {
  name: "App",
  components: {
    TitleElement,
  },

  data() {
    return {
      pokerApi: [],
      txtPokemon: "",
      baseUrl: "https://pokeapi.co/api/v2/",
    };
  },

  methods: {
    getPokerApi() {
      fetch(`${this.baseUrl}`)
        .then((response) => response.json())
        .then((respApi) => {
          console.log(respApi);
          this.pokerApi = [];
          this.pokerApi.push(respApi);
        });
    },
    fieldValidade() {
      if (this.txtPokemon) {
        return console.log("hellow");
      }
    },
  },
};
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
.content-select {
  margin: 20px 20px 10px;
}
.select-element {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 200px;
  height: 22px;
  margin: 10px;
}
.btn {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 13px;
  border: solid 1px #2c3e50;
  width: 120px;
  height: 23px;
  color: white;
  background-color: rgb(20, 130, 219);
}
.btn:hover {
  background-color: rgb(68, 163, 241);
}
</style>
