<template>
  <div class="hola">
    <h1>Hola mundo</h1>
    <div id="app">
      <h1>Bitcoin Price</h1>
      <div v-for="(item, info) in info" :key="item.id">
        {{ info }}.. {{ item.description }}. {{ item.symbol }}. {{ item.rate }}.
        {{ item.tasa }}:
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      info: null,
    };
  },
  mounted() {
    axios
      .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then((response) => (this.info = response.data.bpi));
  },
  filters: {
    currencydecimal(value) {
      return value.toFixed(2);
    },
  },
};
</script>
