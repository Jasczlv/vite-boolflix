<script>
import axios from "axios";
export default {
  data() {
    return {
      inputValue: "ritorno al futuro",
    };
  },
  methods: {
    getApi() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=a9f93794d83843cad47d4bcbc4f86888&query=${this.inputValue}`
        )
        .then((res) => {
          console.log(res);
          const data = res.data.results[0];
          const name = data.title;
          const originalName = data.original_title;
          const lang = data.original_language;
          const rating = data.vote_average;
          console.log(name, originalName, lang, rating);
        });
    },
  },
  mounted() {
    this.getApi();
  },
};
</script>
<template>
  <h1>Boolflix</h1>
  <input type="text" placeholder="Cerca film" v-model="inputValue" />
  <button @click="getApi">send</button>
</template>
<style></style>
