<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <SearchGif :text="text" />
    <img :src="gifs" alt="" />
  </div>
</template>

<script>
import axios from "axios";
import SearchGif from "@/components/SearchGif.vue";

export default {
  name: "App",
  components: {
    SearchGif,
  },

  data: () => ({
    API_KEY: process.env.VUE_APP_GIF,
    text: "",
    apiGif: "https://api.giphy.com/v1/gifs/search?",
    gifs: null,
  }),

  created() {
    axios
      .get(`${this.apiGif}api_key=${this.API_KEY}&limit=1&q=hol`)
      .then(
        (response) => (this.gifs = response.data.data[0].images.original.url)
      );
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
