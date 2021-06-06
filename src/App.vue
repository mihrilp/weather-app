<template>
  <div id="app">
    <h1 class="title">WEATHER APP</h1>
    <div class="search-bar">
      <img class="icon" src="./assets/images/search_icon.svg" alt="" />
      <input
        type="text"
        class="search-input"
        placeholder="Choose your city"
        v-model="city"
        @keypress="getWeather"
      />
    </div>
    <div class="results">
      <div>
        <Card
          :city="results.name"
          :country="results.name"
          :weather="weather.main"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Card from "./components/Card.vue";

export default {
  name: "App",
  data() {
    return {
      city: "",
      results: {},
      weather: {},
    };
  },
  methods: {
    setResults(results) {
      this.results = results;
      console.log(this.results);
      this.weather = results.weather[0];
      this.city = "";
    },
    getWeather(e) {
      if (e.key == "Enter") {
        fetch(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=${process.env.VUE_APP_API_KEY}`
        )
          .then((response) => response.json())
          .then((data) => this.setResults(data));
      }
    },
  },
  components: {
    Card,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
  background-image: url("./assets/images/3.jpg");
}

.title {
  font-family: "Sigmar One", cursive;
  color: #ffff;
  font-weight: bold;
  text-align: center;
  -webkit-text-stroke: 1.5px #3a4586;
}

.search-bar {
  width: 30%;
  margin: 50px;
  align-items: center;
  display: flex;
  flex-direction: row;
  justify-content: center;
  background-color: rgb(255, 255, 255);
  padding: 10px 20px 10px 20px;
  transition: all 0.2s ease 0s;
  border-radius: 20px;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 6px -1px,
    rgba(0, 0, 0, 0.06) 0px 2px 4px -1px;
}

.search-input {
  width: 100%;
  border: none;
  font-size: 16px;
}

.icon {
  margin-right: 8px;
}

::placeholder {
  color: rgb(197, 197, 197);
  opacity: 1;
}
</style>
