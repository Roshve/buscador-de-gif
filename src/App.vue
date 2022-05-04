<template>
  <div id="app">
    <input type="text" v-model="text" @keyup="peticion" />
    <div v-for="(gif, index) in gifs" :key="index">
      <img :src="gif.images.original.url" alt="" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",

  data: () => ({
    API_KEY: process.env.VUE_APP_GIF,
    text: "",
    apiGif: "https://api.giphy.com/v1/gifs/search?",
    gifs: null,
  }),

  methods: {
    async peticion() {
      if (this.text.length > 0) {
        try {
          await axios
            .get(`${this.apiGif}api_key=${this.API_KEY}&limit=2&q=${this.text}`)
            .then((response) => (this.gifs = response.data.data));
        } catch (e) {
          console.log(e);
        }
      }
    },
  },
};
</script>

<style>
input {
  height: 30px;
  width: 600px;
  border: 2px solid red;
  border-radius: 4px;
  outline: none;
  padding-left: 10px;
  font-size: 20px;
}

input:focus {
  border-color: blue;
}
</style>
