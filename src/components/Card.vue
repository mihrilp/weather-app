<template>
  <div id="Card" class="results">
    <div class="date">{{ day }},{{ date }}</div>
    <p>{{ city }}, {{ country }}</p>
    <p>{{ weather }}</p>
  </div>
</template>

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
  props: {
    city: String,
    country: String,
    weather: String,
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
