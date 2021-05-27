<template>
  <div id="app">
    <div class="search-bar">
      <input
        type="text"
        class="search-input"
        placeholder="Choose your city"
        v-model="city"
        @keypress="fetchAPIData"
      />
    </div>
    <div class="weather">
      <p>{{ city }}, {{ country }}</p>
      <p>{{ description }}</p>
      <p>{{ lowTemp }}</p>
      <p>{{ highTemp }}</p>
      <p>feelsLike: {{ feelsLike }}</p>
      <p>humidity: {{ humidity }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      city: "",
      country: "UK",
      description: "Clouds everywhere",
      lowTemp: "19",
      highTemp: "30",
      feelsLike: "20",
      humidity: "55",
    };
  },
  methods: {
    fetchAPIData(e) {
      if (e.key == "Enter") {
        console.log(process.env.VUE_APP_API_KEY);
        fetch(
          `https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=${process.env.VUE_APP_API_KEY}`
        )
          .then((response) => response.json())
          .then((data) => console.log(data));
      }
    },
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
