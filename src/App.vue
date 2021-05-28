<template>
  <div id="app">
    <div class="search-bar">
      <input
        type="text"
        class="search-input"
        placeholder="Choose your city"
        v-model="city"
        @keypress="getWeather"
      />
    </div>
    <div class="results">
      <div></div>
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
    };
  },
  methods: {
    setResults(results) {
      this.results = results;
    },
    getWeather(e) {
      if (e.key == "Enter") {
        return Card;
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
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

.search-bar {
  margin: 50px;
  width: 100%;
  align-items: center;
  display: flex;
  flex-direction: row;
  justify-content: center;
}
.search-input {
  display: block;
  width: 40%;
  padding: 15px;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  transition: 0.4s;
}
</style>
