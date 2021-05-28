<template>
  <div id="Card" class="results">
    <p>oldu</p>
  </div>
</template>

<!--
<script>
import moment from "moment";
export default {
  name: "Card",
  data() {
    return {
      day: moment().format("dddd"),
      date: moment().format("LL"),
      results: {},
    };
  },
  methods: {
    setResults(results) {
      this.results = results;
    },
    fetchAPIData(e) {
      if (e.key == "Enter") {
        fetch(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=${process.env.VUE_APP_API_KEY}`
        )
          .then((response) => response.json())
          .then((data) => this.setResults(data));
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
</style>
-->
