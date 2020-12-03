<template>
  <div class="container">
    <TitleElement msg="Get Pokemons API " />
    <div class="content-select">
      <select v-model="selected" class="select-element" name="Select Search">
        <option disabled value="">Select Item</option>
        <option class="opName" value="Name">Name</option>
        <option class="opId" value="Id">Id</option>
        <option class="opAbility" value="Ability">Ability</option>
      </select>
      <button class="btn" @click="getPokerName()">Search</button>
      <ul>
        <li
          v-for="index in pokerApi"
          :key="index"
          class="pokerNamePrint"
        >
          {{ index }}
        </li>
      </ul>
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
      selected: "",
      typedPoker: "",
      baseUrl: "https://pokeapi.co/api/v2/",
    };
  },

  methods: {
  
    getPokerApi() {
      fetch(`${this.baseUrl}pokemon`)
      .then((response) => response.json())
      .then((respApi) => {
        console.log(respApi);
        this.pokerApi = [];
        this.pokerApi.push(respApi.results)
        console.log(this.selected)
      });
    },
    getPokerName(){
      if (this.selected === "Name") {
       this.typedPoker = prompt('what poker name?')
        console.log(this.typedPoker)
      }
    },
  },
};
</script>

<style>

ul, li {
  list-style-type: none;
}
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
  height: 100%;
  box-shadow: 0 8px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 40px 0 rgba(0, 0, 0, 0.19);
}
.content-select {
  margin: 20px 20px 10px;
  padding: 3px;
}
.select-element {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 14px;
  font-weight: bolder;
  width: 200px;
  height: 25px;
  margin: 10px;
  background-color: #f1f1f1;
  border: 1px solid #f1f1f1;
  cursor: pointer;
}
.select-element:hover {
  border: 1px solid rgb(255, 193, 23);
}
.btn {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-weight: bold;
  font-size: 14px;
  border: solid 1px #2c3e50;
  width: 120px;
  height: 27px;
  background-color: rgb(255, 193, 23);
  color: black;
}
.btn:hover {
  background-image: linear-gradient(rgb(255, 226, 164), rgb(255, 193, 23));
  color: black;
}
.pokerNamePrint {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-weight: bold;
  font-size: 12px;
  color: rgb(255, 193, 23);
}
</style>
